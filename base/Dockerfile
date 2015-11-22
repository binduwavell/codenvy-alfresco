FROM binduwavell/codenvy-alfresco-shellinabox:0.1

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

# install and setup java
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

# install and setup maven
RUN wget -qO- \
    "http://mirror.metrocast.net/apache/maven/maven-3/3.3.3/binaries/apache-maven-3.3.3-bin.tar.gz" | sudo tar -zx -C /opt/
    
ENV M2_HOME /opt/apache-maven-3.3.3
RUN echo "export M2_HOME=$M2_HOME" >> /home/user/.bashrc
ENV MAVEN_HOME /opt/apache-maven-3.3.3
RUN echo "export MAVEN_HOME=$MAVEN_HOME" >> /home/user/.bashrc
ENV PATH $M2_HOME/bin:$PATH
RUN echo "export PATH=$PATH" >> /home/user/.bashrc

# install setup npm and yeoman
RUN wget -qO- "https://deb.nodesource.com/setup_5.x" | sudo bash - && \
    sudo apt-get install -y python git ruby-full rubygems nodejs && \
    sudo ln -sf /usr/bin/nodejs /usr/bin/node && \
    sudo npm install -g yo && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV HOME /home/user 

RUN mkdir /home/user/application /tmp/application
    
WORKDIR /home/user/application
