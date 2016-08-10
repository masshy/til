## environment

開発環境や本番環境などで設定を分けられる。

```
> php codecept.phar generate:environment development
```

`development`環境を生成。

### 設定ファイル(<env>.yml)の書き方

module, helper単位で設定を書く。

```
modules:
    config:
        ModuleA:
            A: 'a'
            B: 23
        \Helper\ExampleHelper:
            FOO: 'bbb'
            BAR: 123
```

\<suitename\>.suite.ymlのconfigは上書きされる。

* Example.suite.yml

```
class_name: ExampleTester
modules:
    enabled:
        - \Helper\ExampleHelper
        - Asserts
        - REST:
            depends: PhpBrowser
config:
    \Helper\ExampleHelper:
        FOO: 'aaa'
```


* development.php

```
modules:
    config:
        \Helper\ExampleHelper:
            FOO: 'bbb'
            BAR: 123
```

テスト実行時のオプションによって読み込まれるconfigが異なる。
この場合、読み込まれるのはExample.suite.ymlのconfig。

```
> php codecept.phar run example
```

`--env`オプションをつけると読み込むconfigを指定できる。

```
> php codecept.phar run example --env development
```

`FOO => 'bbb'`に上書きされ新しく`BAR => 123`が作られる。


