FROM debian:jessie

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN apt-get update && \
    apt-get -y install sudo procps wget unzip mc gcc make && \
    echo "%sudo ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    useradd -u 5001 -G users,sudo -d /home/user --shell /bin/bash -m user && \
    echo "secret\nsecret" | passwd user && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN usermod -u 1000 user

USER user

EXPOSE 4200

ENV CODENVY_WEB_SHELL_PORT 4200

ADD entrypoint.sh /entrypoint.sh

ADD shellinabox.zip /opt/shellinabox.zip

RUN sudo chown user:user -R /opt && \
    cd /opt && unzip shellinabox.zip && \
    sudo chmod 755 /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

# arrange for shellinabox to use tmux for session persitence
# also get curl so we have it for later
ADD _tmux.conf /home/user/.tmux.conf
ENV SHELL_IN_A_BOX_SERVICE /:user:users:/home/user:/usr/bin/tmux -2 new -A -s runner
RUN sudo apt-get update && \
    sudo apt-get install -y tmux curl && \
    sudo chmod 755 /entrypoint.sh && \
    sudo apt-get clean && \
    sudo rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
