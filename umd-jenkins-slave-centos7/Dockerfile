FROM centos:centos7 
MAINTAINER Pablo Orviz <orviz@ifca.unican.es>

USER root
RUN yum -y install git sudo
RUN sed -i '/Defaults *requiretty/s/^/#/' /etc/sudoers

RUN yum -y install openssh-server java-1.7.0-openjdk
RUN sed -i 's|session    required     pam_loginuid.so|session    optional     pam_loginuid.so|g' /etc/pam.d/sshd
RUN mkdir -p /var/run/sshd
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N ''
RUN ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key -N ''

RUN useradd -ms /bin/bash jenkins
RUN echo "jenkins:jenkins" | chpasswd
RUN sed -i '/root\tALL=/a jenkins ALL=(ALL) NOPASSWD: ALL' /etc/sudoers

ADD https://raw.githubusercontent.com/egi-qc/umd-verification/master/bin/utils/prepare_centos7.sh /tmp/
RUN bash /tmp/prepare_centos7.sh

RUN yum -y install python-jinja2
RUN yum -y install openssl openssl-devel

ADD https://raw.githubusercontent.com/egi-qc/umd-verification/master/requirements.txt /tmp/
RUN pip install -r /tmp/requirements.txt

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
