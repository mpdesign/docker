FROM python:2.7
MAINTAINER linqm <linqm@feiyu.com>


# source
RUN echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib\ndeb-src http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib" | tee /etc/apt/sources.list


RUN apt update && apt install -y net-tools openssh-server iputils-ping wget unzip vim less python-setuptools gcc python-dev libffi-dev gfortran openssl libblas-dev liblapack-dev libatlas-dev libmysqld-dev

RUN easy_install pip

RUN pip install MySQL-python DBUtils redis paramiko numpy 

# RUN pip install nose scipy matplotlib

# 时区
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# 启动ssh
RUN service ssh start

# 创建ssh用户，useradd -d /home/analysis -o -u 0 -g 0 analysis
# root权限用户，需要修改 /etc/ssh/sshd_config
# PermitRootLogin without-password 修改为 PermitRootLogin yes

# CMD ["python"]
