FROM phusion/baseimage:0.9.19
MAINTAINER Jeff Liu <jeff.l.crazy@gmail.com>

# Set locale.
RUN locale-gen --no-purge en_US.UTF-8
ENV LC_ALL en_US.UTF-8

ENV DEBIAN_FRONTEND noninteractive

# Install coturn.
RUN set -x \
	&& sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list \
	&& apt-get update \
	&& apt-get -y install coturn

RUN mkdir /etc/service/coturn
COPY coturn.sh /etc/service/coturn/run
COPY coturn.logrotate /etc/logrotate.d/coturn

# Fix logrotate.
RUN sed -i 's/su root syslog/su root adm/g' /etc/logrotate.conf

# Get rid of sshd.
RUN rm -rf /etc/service/sshd && rm -f /etc/my_init.d/00_regen_ssh_host_keys.sh

# Allow volume.
VOLUME = /srv

# Use baseimage-docker's init system.
CMD ["/sbin/my_init"]

# Clean up APT when done.
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
