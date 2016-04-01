# Based on gmauro/ubuntu-ansible
FROM gmauro/ubuntu-ansible
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

ENV IRODSVERSION 4.1.8
ENV IRODSPLUGINSVERSION 1.8
ENV IRODSFTP ftp://ftp.renci.org/pub/irods
ENV IRODS_SERVICE_ACCOUNT irods

ENV DB_HOST localhost

RUN git clone https://github.com/gmauro/irods-in_place /tmp/irods-in_place
WORKDIR /tmp/irods-in_place
RUN ansible-playbook icat.yml

RUN apt-get update && apt-get install -y supervisor

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Add VOLUMEs to allow backup of config, logs and databases
VOLUME ["/etc", "/home", "/var/log", "/var/lib"]

EXPOSE 1247

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]

WORKDIR /home/$IRODS_SERVICE_ACCOUNT
USER $IRODS_SERVICE_ACCOUNT