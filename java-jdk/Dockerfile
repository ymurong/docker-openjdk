# AlpineLinux with a glibc-2.21 and Oracle Java 8

FROM alpine:3.3
MAINTAINER 'Aeon Builds <builds+dockerhub@aeon.io>'

# Install cURL
RUN apk update && apk --update add curl ca-certificates tar && \
    curl -Ls https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk > /tmp/glibc-2.21-r2.apk && \
    apk add --allow-untrusted /tmp/glibc-2.21-r2.apk

# Java Version
ENV JAVA_VERSION_MAJOR 8
ENV JAVA_VERSION_MINOR 66
ENV JAVA_VERSION_BUILD 17
ENV JAVA_PACKAGE       jdk

# Download and unarchive Java
RUN mkdir /opt && curl -jksSLH "Cookie: oraclelicense=accept-securebackup-cookie"\
  http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-b${JAVA_VERSION_BUILD}/${JAVA_PACKAGE}-${JAVA_VERSION_MAJOR}u${JAVA_VERSION_MINOR}-linux-x64.tar.gz \
    | tar -xzf - -C /opt &&\
    ln -s /opt/jdk1.${JAVA_VERSION_MAJOR}.0_${JAVA_VERSION_MINOR} /opt/java &&\
    rm -rf /opt/java/*src.zip \
           /opt/java/lib/missioncontrol \
           /opt/java/lib/visualvm \
           /opt/java/lib/*javafx* \
           /opt/java/jre/lib/plugin.jar \
           /opt/java/jre/lib/ext/jfxrt.jar \
           /opt/java/jre/bin/javaws \
           /opt/java/jre/lib/javaws.jar \
           /opt/java/jre/lib/desktop \
           /opt/java/jre/plugin \
           /opt/java/jre/lib/deploy* \
           /opt/java/jre/lib/*javafx* \
           /opt/java/jre/lib/*jfx* \
           /opt/java/jre/lib/amd64/libdecora_sse.so \
           /opt/java/jre/lib/amd64/libprism_*.so \
           /opt/java/jre/lib/amd64/libfxplugins.so \
           /opt/java/jre/lib/amd64/libglass.so \
           /opt/java/jre/lib/amd64/libgstreamer-lite.so \
           /opt/java/jre/lib/amd64/libjavafx*.so \
           /opt/java/jre/lib/amd64/libjfx*.so

# Set environment
ENV JAVA_HOME /opt/java
ENV PATH ${PATH}:${JAVA_HOME}/bin
