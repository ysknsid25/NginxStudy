FROM rockylinux/rockylinux:8.4

RUN yum -y update

RUN yum -y install nginx
RUN systemctl enable nginx

RUN mkdir -p /framefork/www/html