## OAuthとは

- アプリケーションに対して安全にアクセスできるようにするためのプロトコルのこと。
- 安全にアクセス権限を提供するためのもの。
- GitHub、twitter、facebookなどを使用してログインできるようにするためのもの。

## OmniAuthとは

ユーザ人諸機能を提供するためのベースとなるgemのこと。

## Oauthを使用したusersテーブルのカラムについて

下記コマンドを実行してusersテーブルを作成したら

```ruby
rails g model user provider:string uid:string name:string image_url:string
```

以下のようなマイグレーションファイルが生成される。

```ruby
class CreateUsers < ActiveRecord::Migration[6.0]
  def change
    create_table :users do |t|
      t.string :provider,  null: false
      t.string :uid,       null: false
      t.string :name,      null: false
      t.string :image_url, null: false
      t.timestamps
    end
  end

  add_index :users, %i[provider uid], unique: true
end
```

**provider**・・・OmniAuthの認証で使用するプロバイダ名（twitter、facebook、GitHubなど）

**uid**・・・provider毎に与えられるユーザ識別用の文字列。

**name**・・・（それぞれでアプリで使用している）ユーザ名

**image_url**・・・（それぞれのアプリで使用している）アイコン画像のURL
                  ※ActiveStorageを使用する場合はこのカラムが不要

<br>

生成されたマイグレーションファイルに**NOT NULL制約**と**ユニークインデックス**を追加しておく。

NULLになるケースがないカラムに対して付与することで、想定外のデータ不整合を回避することができる。

また、add_indexの中で記述している、unique: trueを付与することで、全く同じユーザIDでは登録できないようにしてくれる。