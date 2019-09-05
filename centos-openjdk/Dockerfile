FROM centos:6

RUN rpm -Uvh http://repo.mysql.com/mysql-community-release-el6-5.noarch.rpm \
    && yum install -y \
    mysql-server java-1.7.0-openjdk vim-minimal zip unzip tar gzip mc ntp \
    openssh openssh-server tcl tix tk tkinter requests rsh-server xinetd dhcp \
    sudo \
    && yum clean all
