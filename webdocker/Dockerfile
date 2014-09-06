#
# Ubuntu Dockerfile
#
# https://github.com/dockerfile/ubuntu
#
# Test comment

# Pull base image.
FROM ubuntu:14.04

# Install.
RUN \
  sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y build-essential && \
  apt-get install -y software-properties-common && \
  apt-get install -y byobu curl git htop man unzip vim wget


# Install Java.
RUN \
  echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java7-installer
  apt-get install openjdk-7-jdk

#install ruby
RUN \curl -sSL https://get.rvm.io | bash -s stable --ruby
RUN /bin/bash -l -c rvm requirements
RUN /bin/bash -l -c rvm install 2.1.2

ENV PATH /usr/local/rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
RUN /bin/bash -l -c rvm use 2.1.2 --default
#Install jruby
rvm install jruby
ENV PATH /opt/rubies/jruby/bin:$PATH


#Install ffmepg
RUN add-apt-repository ppa:jon-severinsson/ffmpeg
RUN apt-get update
RUN apt-get install -y ffmpeg
RUN apt-get install -y frei0r-plugins

#Install imagemagick
RUN apt-get install -y imagemagick

#Install Prince
RUN apt-get install libgif4
RUN wget http://www.princexml.com/download/prince_9.0-5_ubuntu14.04_amd64.deb
RUN dpkg -i prince_9.0-5_ubuntu14.04_amd64.deb

#Install RabbitMQ 
RUN apt-get install -y rabbitmq-server

#Install Sphinx
RUN  apt-get install -y sphinxsearch


# Add files.
#ADD root/.bashrc /root/.bashrc
#ADD root/.gitconfig /root/.gitconfig
#ADD root/scripts /root/scripts

# Set environment variables.
ENV HOME /root

# Define working directory.
WORKDIR /root

# Define default command.
CMD ["bash"]
