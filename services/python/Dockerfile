FROM python:2.7
MAINTAINER linqm <linqm@feiyu.com>


# source
RUN echo "deb http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-updates main non-free contrib\ndeb-src http://mirrors.163.com/debian/ jessie-backports main non-free contrib\ndeb http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib\ndeb-src http://mirrors.163.com/debian-security/ jessie/updates main non-free contrib" | tee /etc/apt/sources.list


RUN apt update && apt install -y net-tools iputils-ping wget unzip vim python-setuptools gcc python-dev libffi-dev gfortran openssl libblas-dev liblapack-dev libatlas-dev libmysqld-dev

RUN easy_install pip

RUN pip install MySQL-python DBUtils redis paramiko numpy 

# RUN pip install nose scipy matplotlib


# CMD ["python"]
