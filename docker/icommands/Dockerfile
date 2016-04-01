# Based on gmauro/ubuntu-ansible
FROM gmauro/ubuntu-ansible
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

ENV IRODSVERSION 4.1.8
ENV IRODSFTP ftp://ftp.renci.org/pub/irods
ENV IUSER iuser

RUN git clone https://github.com/gmauro/irods-in_place /tmp/irods-in_place
WORKDIR /tmp/irods-in_place
RUN ansible-playbook icommands.yml

RUN apt-get update && apt-get install -y supervisor
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]

WORKDIR /home/$IUSER
USER $IUSER