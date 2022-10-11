# 元にするイメージ
FROM rockylinux/rockylinux:8.4

# カーネル・ライブラリの更新
RUN yum -y update

# 使いたいソフトをインストール
RUN yum install -y wget

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
RUN htpasswd -cb /etc/nginx/htpasswd authuser hogehoge

# コンテナを動かすためのユーザー
RUN useradd webuser && echo webuser:ysknsid25 | chpasswd
RUN chown -R webuser:webuser /framework/
RUN chmod 755 -R /etc/nginx/
RUN chown -R webuser:webuser /etc/nginx/
#USER webuser

# PHP FPM
RUN yum install -y php-fpm
RUN yum install -y php-mysqlnd

# wordpressのインストール
RUN mkdir -p  /framework/www/wordpress
RUN cd /framework/www/wordpress/
RUN wget https://ja.wordpress.org/latest-ja.tar.gz
RUN tar xfz latest-ja.tar.gz
RUN chown -R nginx. wordpress

# PHP-FPMで扱うソケットが作られないので、作る
RUN mkdir -p /var/run/php-fpm
RUN touch /var/run/php-fpm/php-fpm.sock
RUN chmod 755 /var/run/php-fpm/php-fpm.sock
RUN chown webuser:webuser /var/run/php-fpm/php-fpm.sock

# これを参考にwww.confの設定を変えた
# https://pig-log.com/nginx-php-fpm-error/