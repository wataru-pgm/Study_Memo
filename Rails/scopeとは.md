# scopeとは

データを絞り込みたいときに使用する。

## メリット

コードが長ったらしくなるのを防ぎ、一つのメソッドとして定義することができる。

## scopeメソッドの基本

書き方としては下記のように定義する

```ruby
Class モデル名　< ApplicationRecord
  scope :スコープの名前, -->　{ 条件式 }
end
```

## 使い方の説明

例えば以下のようなコードがあったとします。

```ruby
Board.order(id: desc).limit(5)
```

この記述をいろんなところで使用する場合、

記述量が多くなるし、可読性が落ちてしまう。

そんなときに使用するのがscope。

上記と同じ式を一つのメソッドとして定義できる(ここでいうrecent)

●board.rb

```ruby
Class Board < ApplicationRecord
  scope :recent, --> { order(id: :desc).limit(5) }
end
```

●boards_controller

```ruby
class BoardsController < ApplicationController

def index
  @boards = Board.recent
end
```

上記のように記述するとコントローラ側でもBoard.recentが使えるようになるので簡潔に記述することができる。

またスコープに引数を渡すこともできる

●board.rb

```ruby
scope :recent, -->  (count) { order(id: :desc).limit(count) }
```

●boards_controller

```ruby
class BoardsController < ApplicationController

def index
  @boards = Board.recent(8)
end
```

これでコントローラ側で Board.currnet(8) と記述すれば最新の8件を取得できるようになる。