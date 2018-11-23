FROM openpai/pai.example.tensorflow:stable 

MAINTAINER Yueqing Zhuang "https://github.com/zhuangyueqing"

RUN rm /etc/apt/sources.list.d/cuda.list && rm /etc/apt/sources.list.d/nvidia-ml.list
RUN apt-get update
RUN apt-get -y install sudo
RUN apt-get install -y openssh-server

RUN useradd -d /home/zhuangyueqing -ms /bin/bash -g root -G sudo -p zhuangyueqing zhuangyueqing
RUN echo 'zhuangyueqing:12345678' |chpasswd

RUN mkdir /var/run/sshd
RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN mkdir /root/.ssh
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 22
#CMD ["/usr/sbin/sshd", "-D"]
