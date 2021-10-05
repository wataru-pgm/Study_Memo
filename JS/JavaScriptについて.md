# JavaScriptについて


## JSって何ができる？

・アニメーション

・ユーザー操作に合わせて見た目を変えることができる

・API

・バックエンドでも実行できる

## ブラウザのconsoleでチェック

```document.getElementById("input")```

formタグの中に書いてるinputタグの中身の情報を取得することができる

```document.getElementById("input").value```

末尾に.valueをつけることで、ブラウザ上でinputタグの中に入力した値を取得することができる

## index.htmlからデータを取りたい

### 変数とは

データの入れ物、ラベル

let・・・値の再代入ができる

const・・・値の再代入ができないようにする（例えば税率とか）

var ・・・varはletと同じ、昔の記法、今は使わない

### 関数とは

一連の処理を一つにまとめたもの

function と書くことで関数として定義する

### addEventListerとは

特定のイベントが起きたときにjavaScriptの処理を追加するためのブラウザAPIの機能のこと（JavaScriptの機能ではない）

下記のように書く

```jsx
ターゲット.addEventListener(イベント名、関数);

form.addEventListener("submit",

function () {
 console.log();
})

function () {
 console.log();
}
```