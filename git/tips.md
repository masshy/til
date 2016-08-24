# tips

「慌てず騒がず落ち着いて」

## .gitignoreを反映させる

gitで色々やってて無視したいファイルができたら、.gitignoreに当該ファイルを追加し反映させる。

```
> git rm -r --cached <filename>
```

キャッシュを削除したので、再度コミットするとファイルが消える。

## リモートのブランチ名を変更する

* [ローカルとリモートのブランチ名を変更する](https://gist.github.com/naosim/e2ee53c04e2d80eb3362)
* [git でリモートブランチの名前を変更する](http://kidooom.hatenadiary.jp/entry/20140204/1391522618)

## コミットメッセージを修正

以下のコマンドを打つとvimが開いて、そこで修正する。

```
> git commit --amend
```


