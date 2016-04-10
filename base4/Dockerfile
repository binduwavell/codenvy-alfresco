FROM codenvy/alpine_jdk8

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

ADD _tmux.conf /home/user/.tmux.conf
RUN sudo apk add --no-cache nodejs tmux && \
    sudo npm install -g npm && \
    sudo npm install -g yo
