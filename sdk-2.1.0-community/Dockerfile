FROM binduwavell/codenvy-alfresco-base:0.3

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN mkdir /home/user/tmp && \
    cd /home/user/tmp && \
    mvn archetype:generate -DinteractiveMode=false \
        -DarchetypeGroupId=org.alfresco.maven.archetype -DarchetypeArtifactId=alfresco-allinone-archetype -DarchetypeVersion=2.1.0 \
        -DgroupId=com.example -DartifactId=deleteme -Dversion=1.0.0-SNAPSHOT && \
    cd deleteme && \
    mvn package -DskipTests && \
    chmod 755 run.sh && \
    timeout 15m ./run.sh ; \
    cd /home/user && \
    rm -rf tmp
