FROM codenvy/shellinabox

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN wget \
    --no-cookies \
    --no-check-certificate \
    --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    -qO- \
    "http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz" | sudo tar -zx -C /opt/
     
ENV JAVA_HOME /opt/jdk1.8.0_45
RUN echo "export JAVA_HOME=$JAVA_HOME" >> /home/user/.bashrc
ENV PATH $JAVA_HOME/bin:$PATH
RUN echo "export PATH=$PATH" >> /home/user/.bashrc

# install some components
RUN sudo apt-get update && \
    sudo apt-get install -y python git ruby-full rubygems npm && \
    sudo ln -sf /usr/bin/nodejs /usr/bin/node && \
    sudo npm install -g yo

ENV HOME /home/user 

RUN mkdir /home/user/application /tmp/application
    
WORKDIR /home/user/application