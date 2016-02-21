FROM aeonproject/base
MAINTAINER 'Aeon Builds <builds+dockerfile@aeon.io>'

ENV JAVA_VERSION_MAJOR 8
ENV JAVA_VERSION_MINOR 72
ENV JAVA_VERSION_BUILD 15
ENV JAVA_VERSION_REVIS r1

RUN echo '@edge http://nl.alpinelinux.org/alpine/edge/main' >> /etc/apk/repositories \
 && echo '@community http://nl.alpinelinux.org/alpine/edge/community' >> /etc/apk/repositories \
 && apk update && apk upgrade \
 && apk add openjdk8@community=${JAVA_VERSION_MAJOR}.${JAVA_VERSION_MINOR}.${JAVA_VERSION_BUILD}-${JAVA_VERSION_REVIS} \
 && rm -rf /var/cache/apk/*

ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV PATH ${PATH}:${JAVA_HOME}/bin

ENTRYPOINT [ 'java' ]
