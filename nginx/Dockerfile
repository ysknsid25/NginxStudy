# 元にするイメージ
FROM rockylinux/rockylinux:8.4

# カーネル・ライブラリの更新
RUN yum -y update

# nginx のインストールと自動起動の設定。静的ホスティングの場所の設定
RUN yum -y install nginx
RUN systemctl enable nginx
RUN mkdir -p /framework/www/html

# コンテナを動かすためのユーザー
RUN useradd webuser
RUN chown -R webuser:webuser /framework/
USER webuser