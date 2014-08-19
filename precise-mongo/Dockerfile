# Mongo 2.4.1 on Ubuntu 12.04

FROM       ubuntu:12.04
MAINTAINER Trent Ogren <tedwardo2@gmail.com>

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | tee /etc/apt/sources.list.d/10gen.list

RUN apt-get update
RUN apt-get install -y -q mongodb-10gen=2.4.1
#RUN echo "mongodb-10gen hold" | sudo dpkg --set-selections

VOLUME ["/data/db"]

EXPOSE 27017

ENTRYPOINT ["usr/bin/mongod"]
