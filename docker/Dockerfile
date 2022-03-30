FROM node:14-stretch

MAINTAINER clay<clay@gmail.com>

# 拷贝一键安装脚本
ADD debian-install.sh /root/debian-install.sh

# 更换软件源
RUN cp /etc/apt/sources.list /etc/apt/sources.list.bak && \
    echo "deb http://mirrors.aliyun.com/debian/ stretch main non-free contrib" > /etc/apt/sources.list && \
    echo "deb http://mirrors.aliyun.com/debian-security stretch/updates main" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.aliyun.com/debian/ stretch-updates main non-free contrib" >> /etc/apt/sources.list && \
    echo "deb http://mirrors.aliyun.com/debian/ stretch-backports main non-free contrib" >> /etc/apt/sources.list

# 安装依赖
RUN apt-get -y update && apt-get -y upgrade && \
    apt-get -y install vim tree htop apt-utils net-tools telnet wget curl && \
    apt-get -y install autoconf git build-essential libpcre3 libpcre3-dev zlib1g zlib1g.dev openssl libssl-dev && \
    apt-get -y autoclean && apt-get -y autoremove

# 执行一键安装脚本
RUN bash /root/debian-install.sh

# 启动服务
CMD cd ~/luban-h5 && bash luban-h5.sh start \
    && echo "started" > /var/log/luban.log \
    && tail -f -n 20 /var/log/luban.log
