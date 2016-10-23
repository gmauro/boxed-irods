boxed-irods
===========
[![TravisCI](https://api.travis-ci.org/gmauro/boxed-irods.svg?branch=master)](https://travis-ci.org/gmauro/boxed-irods)

iCAT server, installed from iRODS binaries, and postgresql server executed from
 the same host; everything enabled by Ansible.

This repository contains also Dockerfile for iRODS automated
build published to the Docker Hub Registry.

Useful for testing/development.

# Docker images

Docker images of two containers are available at Docker hub:

iCAT server using local postgresql

https://hub.docker.com/r/gmauro/boxed-irods/

iCommands client

https://hub.docker.com/r/gmauro/icommands/

## Requirements

You need [docker-engine](https://docs.docker.com/engine/installation/) and [docker-compose](https://docs.docker.com/compose/install/)

## Quickstart

Clone the repository: `git clone https://github.com/gmauro/boxed-irods.git`

Cd into the docker directory: `cd boxed-irods/docker`

Pull containers images fro the hub: `./dcomp.sh pull`

Only the first time: 

 * Do the first setup of iRODS: `./dcomp.sh run irods /irods_first_setup`

 * Configure iRODs account (default username: iuser, type: rodsuser): `./dcomp.sh
 run irods /irods_config`

Bring up the containers: `./dcomp.sh up -d`

### How to use  iRODS icommands 

Open a bash shell into the icommands container: `docker exec -ti
icommands /bin/bash`

Init the iRODS environment of the user: `iinit`

### Default values

iRODS version: 4.1.8

iRODS service account: irods

iRODS zone: tempZone

iRODS port: 1247

iRODS admin: rods

iRODS user: iuser

db host: localhost

db port: 5432

db name: ICAT

db user: irods

password (for everything): irods123

## Acknowledgments

The work of [pdonorio](https://github.com/pdonorio) at https://github.com/EUDAT-B2STAGE/docker-images has been very useful.
