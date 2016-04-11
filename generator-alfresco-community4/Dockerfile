FROM binduwavell/codenvy4-alfresco-sdk-2.1.1-community:0.2

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN mkdir -p /home/user/tmp && \
    cd /home/user/tmp && \
    git clone https://github.com/binduwavell/generator-alfresco.git && \
    cd /home/user/tmp/generator-alfresco && \
    npm install

CMD bash -c "echo 'Checking if we need to copy node_modules' && test -d /projects/generator-alfresco/node_modules || echo 'Copying node_modules' && cp -r /home/user/tmp/generator-alfresco/node_modules /projects/generator-alfresco" ; \
    cd /projects/generator-alfresco && \
    bash -c "echo 'Checking if we need to npm link' && test -f /projects/generator-alfresco/package.json && echo 'Linking' &&  sudo npm link" ; \
    sudo /usr/bin/ssh-keygen -A && \
    sudo /usr/sbin/sshd -D && \
    tail -f /dev/null
