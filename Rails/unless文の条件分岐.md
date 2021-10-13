# unless分とは
unless分はif分の反対
- if文 → もしも、評価が真(true)だったら〇〇する
- unless文 → もしも、評価が偽(false)だったら〇〇する
の意味になる。


```Ruby
unless 条件式
  条件式の結果が 偽(false) の場合に処理を実行
else
  条件式の結果が 真(true)  の場合に処理を実行
end
```

Rubyでのtrueとfalseの判定条件は、
- false = nil、または false
- true = 上記以外



# パRailsの復習 p305
unless文はfalseがtrueになるので、ifから以下が実行される。
`start_at と end_at` が両方あればtrueだが、unlessがついてるので、
falseがtrueになる、returnされず下のif文が実行される

```Ruby
def start_at_should_be_before_end_at
  # 開始日と終了日が存在すればfalseなので、if文が実行される
  # 開始日と終了日が存在しなければ、returnが実行される
  # unlessは、trueがfalse、falseがtrue
  return unless start_at && end_at
  # 上記と同じ意味になる書き方が下記
  unless start_at && end_at
    return
  end

  if start_at >= end_at
    errors.add(:start_at, "は終了時間よりも前に設定してください")
  end
end
```


# 参考
- https://www.sejuku.net/blog/75155
- https://railsdoc.com/page/conditional_branch