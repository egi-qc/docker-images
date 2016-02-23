FROM evarga/jenkins-slave
MAINTAINER Pablo Orviz <orviz@ifca.unican.es>

USER root
RUN sed -i '/Defaults *requiretty/s/^/#/' /etc/sudoers
RUN sed -i '/root\tALL=/a jenkins ALL=(ALL) NOPASSWD: ALL' /etc/sudoers

RUN apt-get update

ADD https://raw.githubusercontent.com/egi-qc/umd-verification/master/bin/utils/prepare_ubuntu.sh /tmp/
RUN bash /tmp/prepare_ubuntu.sh

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
