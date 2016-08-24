## codeceptionとは

phpのテストツール。実行環境にphpunitを使っている。

## 使い方

codeceptionのテスト単位はスイート(suite)。

codeception.pharをダウンロードしたら、同じディレクトリで`example`スイートを生成。

```
> php codeception.phar generate:suite example
```

`Example`にしても`example`になる。後々スイートを指定する際に`Example`にしてもエラーになる。

## テストの生成

- cept: 非構造的

- cest: 構造的（要はクラス。`_before`,`_after`がない）

```
> php codecept.phar generate:cest example Example

```

## helperの作成

```
> php codecept.phar generate:helper Util
```

## ビルド

helperやyamlを編集したらビルドを忘れずに。

```
> php codecept.phar build
```

## テストの実行

`-d`でテストの詳細を見れる。デバッグモード。

```
> php codecept.phar run example -d
```




