# 元にするイメージ
FROM rockylinux/rockylinux:8.4

# カーネル・ライブラリの更新
RUN yum -y update

# nginx のインストールと自動起動の設定。静的ホスティングの場所の設定
RUN yum -y install nginx
RUN systemctl enable nginx
RUN mkdir -p /framework/www/html
RUN yum -y install logrotate

# rootのパスワードを変えたい
RUN yum -y install passwd
RUN yum -y install sudo

# Basic認証用のパスワード
RUN yum -y install httpd-tools

# コンテナを動かすためのユーザー
RUN useradd webuser && echo webuser:ysknsid25 | chpasswd
RUN chown -R webuser:webuser /framework/
RUN chmod 755 -R /etc/nginx/
RUN chown -R webuser:webuser /etc/nginx/
#USER webuser