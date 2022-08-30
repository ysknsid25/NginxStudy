# 主なコマンド

## 設定ファイルを再読込み

```
nginx -s reload
```

ただし、あらかじめnginxが動いている必要がある。

## 設定ファイル変更後のテスト

```
nginx -t
```

# Nginxの本体設定

/etc/nginx/nginx.conf

## webサーバー用の設定

/etc/nginx/conf.dの下に別途設定ファイルを配置する。

```
# Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;
```

これがあるから上記のような書き方ができている。
nginx.confのserverディレクティブをそのまま残していると、そっちの設定が勝っていることがわかったので、
そっちの設定は全部コメントアウトする。

で、/etc/nginx/conf.d/default.confみたいなファイルを用意して、中身を書き換える。