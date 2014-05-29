# SSH-DOCKER-UBUNTU
#
# VERSION       1

FROM ubuntu:14.04
MAINTAINER koudaiiii "cs006061@gmail.com"

# make sure the package repository is up to date
RUN mv /etc/apt/sources.list /etc/apt/sources.list.original
ADD ./sources.list /etc/apt/sources.list
RUN apt-get clean
RUN apt-get update
#RUN apt-get upgrade -y

#Dev tools for all Docker
RUN apt-get -y install git 
RUN apt-get -y install aptitude

#Install ssh
RUN apt-get -y install openssh-server
RUN mkdir /var/run/sshd
RUN chmod 711 /var/run/sshd


#Setup sshd
RUN  sed -i "s/UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && sed -i "s/UsePAM.*/UsePAM no/g" /etc/ssh/sshd_config

#install user
RUN apt-get -y install passwd sudo

# useradd user,name to koudaiii
RUN useradd --create-home -s /bin/bash koudaiii ;\
    adduser koudaiii sudo ;\
    echo "koudaiii:password" | chpasswd;

# Set .ssh
RUN mkdir -p /root/.ssh;chmod 700 /root/.ssh
ADD ./authorized_keys /root/.ssh/authorized_keys
RUN chown root /root/.ssh/authorized_keys;chmod 600 /root/.ssh/authorized_keys

RUN mkdir -p /home/koudaiii/.ssh;chown koudaiii /home/koudaiii/.ssh; chmod 700 /home/koudaiii/.ssh
ADD ./authorized_keys /home/koudaiii/.ssh/authorized_keys
RUN chown koudaiii /home/koudaiii/.ssh/authorized_keys;chmod 600 /home/koudaiii/.ssh/authorized_keys

# setup sudoers
RUN echo "koudaiii ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers.d/koudaiii
RUN chmod 440 /etc/sudoers.d/koudaiii

# setup timezone
RUN mv /etc/localtime /etc/localtime.org
RUN ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

# setup Supervisor
RUN apt-get install -y supervisor
RUN mkdir -p /var/run/sshd; mkdir -p /var/log/supervisor
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Expose ports.
EXPOSE 22

CMD ["/usr/bin/supervisord"]
