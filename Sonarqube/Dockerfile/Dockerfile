FROM ubuntu:20.04  AS builder

# 安装依赖
RUN apt-get update -y && apt-get upgrade -y && apt-get install  sudo -y
RUN apt-get install wget -y && apt-get install unzip -y

# Install Tools
RUN sudo apt-get install git -y  && apt-get install nano -y

# Install JAVA
RUN DEBIAN_FRONTEND=noninteractive apt install default-jdk -y


FROM builder AS build1

# ADD USER sonar

# build参数
ARG user=sonar

# 添加用户：赋予sudo权限，指定密码
RUN useradd --create-home --no-log-init --shell /bin/bash ${user} \
    && adduser ${user} sudo \
    && echo "${user}:${user}" | chpasswd

# 改变用户的UID和GID
RUN usermod -u 1000 ${user} && usermod -G 1000 ${user}

# 指定容器起来的工作目录
#WORKDIR /home/${user}

# 指定容器起来的登录用户
#USER ${user}

# RUN是构建时执行
RUN echo "${user}" > world.txt


FROM build1 AS build2

# Install Sonarqube

#RUN wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.7.0.2747-linux.zip
ADD sonarqube-9.8.0.63668.zip /opt/sonarqube/sonarqube-9.8.0.63668.zip
RUN unzip -d /opt/sonarqube   /opt/sonarqube/sonarqube-9.8.0.63668.zip
RUN chown -R 1000:1000 /opt/sonarqube/sonarqube-9.8.0.63668

# Install SonarScanner

#WORKDIR /opt/sonarqube
