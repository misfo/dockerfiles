# Minimal Ruby 2.0.0-p247 installation on Ubuntu 12.04
#
# Based on the following Dockerfiles w/ unnecessary packages stripped out:
# * https://github.com/docker-library/docker-buildpack-deps/blob/d47a8bcbc41243939dc4252b32d0fad2bc4f438f/jessie/Dockerfile
# * https://github.com/docker-library/ruby/blob/e9241e3ee0aee4d2365bfcb200994030de93d2ce/2.1/Dockerfile

FROM ubuntu:12.04
MAINTAINER Trent Ogren <tedwardo2@gmail.com>

ENV RUBY_MAJOR 2.0
ENV RUBY_VERSION 2.0.0-p247

RUN apt-get update && apt-get install -y \
		autoconf \
		build-essential \
		libbz2-dev \
		libcurl4-openssl-dev \
		libreadline-dev \
		libssl-dev \
		bison curl ruby procps \
	&& rm -rf /var/lib/apt/lists/*

RUN mkdir -p /usr/src/ruby \
	&& curl -SL "http://cache.ruby-lang.org/pub/ruby/$RUBY_MAJOR/ruby-$RUBY_VERSION.tar.bz2" \
		| tar -xjC /usr/src/ruby --strip-components=1 \
	&& cd /usr/src/ruby \
	&& autoconf \
	&& ./configure --disable-install-doc \
	&& make -j"$(nproc)" \
	&& apt-get purge -y bison ruby \
	&& apt-get autoremove -y \
	&& make install \
	&& rm -r /usr/src/ruby

# skip installing gem documentation
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc

RUN gem install bundler

CMD [ "irb" ]
