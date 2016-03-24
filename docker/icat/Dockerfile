# Based on gmauro/ubuntu-ansible
FROM gmauro/ubuntu-ansible
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN git clone https://github.com/gmauro/irods-in_place /tmp/irods-in_place
WORKDIR /tmp/irods-in_place
RUN ansible-playbook icat.yml

# Add VOLUMEs to allow backup of config, logs and databases
VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]
VOLUME  ["/etc/irods", "/var/lib/irods"]

EXPOSE 1247