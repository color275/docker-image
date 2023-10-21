# docker build -t color275/python-3-8 --platform linux/amd64 .
# docker push color275/python-3-8

FROM centos:8

RUN ln -snf /usr/share/zoneinfo/Asia/Seoul /etc/localtime

RUN cd /etc/yum.repos.d/
RUN sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

# 필요한 패키지 설치
RUN yum update -y && yum install -y gcc openssl-devel bzip2-devel libffi-devel wget make mysql-devel bind-utils ncurses jq

# Python 3.8 다운로드 및 설치
RUN wget https://www.python.org/ftp/python/3.8.0/Python-3.8.0.tgz
RUN tar xzf Python-3.8.0.tgz
RUN cd Python-3.8.0 && ./configure --enable-optimizations && make altinstall

# pip 설치
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
RUN python3.8 get-pip.py
