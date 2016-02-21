FROM aeonproject/base
MAINTAINER 'Aeon Builds <builds+dockerfile@aeon.io>'

RUN echo '@edge http://nl.alpinelinux.org/alpine/edge/main' >> /etc/apk/repositories \
 && echo '@community http://nl.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories \
 && apk update && apk upgrade \
 && apk add openjdk8@community \
 && rm -rf /var/cache/apk/*

ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV PATH ${PATH}:${JAVA_HOME}/bin

ENTRYPOINT [ 'java' ]
