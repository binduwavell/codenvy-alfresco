FROM binduwavell/codenvy4-alfresco-sdk-2.1.1-community:0.2

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN mkdir -p /home/user/tmp && \
    cd /home/user/tmp && \
    git clone https://github.com/binduwavell/generator-alfresco.git && \
    cd /home/user/tmp/generator-alfresco && \
    npm install && \
    sudo npm link

WORKDIR /projects
