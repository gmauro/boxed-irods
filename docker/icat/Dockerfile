# Based on gmauro/ubuntu-ansible
FROM gmauro/ubuntu-ansible
MAINTAINER Gianmauro Cuccuru <gmauro@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN git clone https://github.com/gmauro/irods-in_place /tmp/irods-in_place
#WORKDIR /tmp/irods-in_place
ADD install_irods.sh /install
#RUN ansible-playbook icat.yml

RUN apt-get update && apt-get install -y supervisor

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Add VOLUMEs to allow backup of config, logs and databases
#VOLUME  ["/etc/postgresql", "/var/log/postgresql", "/var/lib/postgresql"]
VOLUME  ["/etc/irods", "/var/lib/irods"]

EXPOSE 1247

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]