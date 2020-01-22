FROM alpine:latest

RUN set -xe \
	# Install required packages for build time. Will be removed when build finishes.
	&& apk add --no-cache --virtual .build-deps gnupg curl tar \
    && curl -SL "https://github.com/apache/incubator-skywalking/releases/download/v3.2.6/skywalking-agent.tar.gz" -o skywalking-agent.tar.gz \
    && tar -xvf skywalking-agent.tar.gz

VOLUME ["/skywalking-agent"]