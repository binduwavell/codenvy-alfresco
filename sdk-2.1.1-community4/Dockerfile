FROM binduwavell/codenvy4-alfresco-base:0.1

MAINTAINER Bindu Wavell <bindu@ziaconsulting.com>

RUN mkdir /home/user/tmp && \
    cd /home/user/tmp && \
    mvn archetype:generate -DinteractiveMode=false \
        -DarchetypeGroupId=org.alfresco.maven.archetype -DarchetypeArtifactId=alfresco-allinone-archetype -DarchetypeVersion=2.1.1 \
        -DgroupId=com.example -DartifactId=deleteme -Dversion=1.0.0-SNAPSHOT && \
    cd deleteme && \
    mvn package -DskipTests && \
    chmod 755 run.sh && \
    timeout -t 1000 -s KILL ./run.sh ; \
    echo temporarily pausing

RUN  cd /home/user && \
     rm -rf /home/user/tmp
