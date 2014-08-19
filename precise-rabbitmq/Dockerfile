# RabbitMQ 3.0.4 on Ubuntu 12.04

FROM ubuntu:12.04
MAINTAINER Trent Ogren <tedwardo2@gmail.com>

RUN apt-get -y update
RUN apt-get install -y wget erlang-nox logrotate

RUN wget --no-check-certificate https://www.rabbitmq.com/releases/rabbitmq-server/v3.0.4/rabbitmq-server_3.0.4-1_all.deb -O /tmp/rabbitmq-server_3.0.4-1_all.deb
RUN dpkg -i /tmp/rabbitmq-server_3.0.4-1_all.deb

RUN rabbitmq-plugins enable rabbitmq_management

# RabbitMQ and RabbitMQ Admin
EXPOSE 5672 15672

ENTRYPOINT ["/usr/sbin/rabbitmq-server"]
