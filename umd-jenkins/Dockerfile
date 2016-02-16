FROM jenkins
MAINTAINER Pablo Orviz <orviz@ifca.unican.es>

USER jenkins 
COPY plugins.txt /usr/share/jenkins/ref/
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/ref/plugins.txt

USER root
RUN apt-get update && apt-get install -y docker.io
