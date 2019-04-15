# "ported" by Adam Miller <maxamillion@fedoraproject.org> from
#   https://github.com/fedora-cloud/Fedora-Dockerfiles
#
# Originally written for Fedora-Dockerfiles by
#   scollier <scollier@redhat.com>

FROM centos:centos7
MAINTAINER The CentOS Project <cloud-ops@centos.org>

ENV PORT 80
ENV HOST 0.0.0.0
ENV PORT 8080
ENV HOST 0.0.0.0
ENV PORT 8880
ENV HOST 0.0.0.0
ENV PORT 443
ENV HOST 0.0.0.0
ENV PORT 8447
ENV HOST 0.0.0.0
ENV PORT 8443
ENV HOST 0.0.0.0
ENV PORT 2121
ENV HOST 0.0.0.0
ENV PORT 2222
ENV HOST 0.0.0.0

RUN yum -y update; yum clean all
RUN yum -y install nano; yum clean all
RUN yum -y install wget; yum clean all
RUN yum -y install libicu60; yum clean all
RUN yum -y install tzdata; yum clean all
RUN yum -y install openssh-server passwd; yum clean all

ADD ./start.sh /start.sh
RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' 

RUN chmod 755 /start.sh
# EXPOSE 22
RUN ./start.sh
ENTRYPOINT ["/usr/sbin/sshd", "-D"]

RUN sh <(curl https://autoinstall.plesk.com/one-click-installer || wget -O - https://autoinstall.plesk.com/one-click-installer)
