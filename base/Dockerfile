FROM ubuntu:16.04

MAINTAINER Sangwon Lee <gamzabaw@gmail.com>

RUN apt-get update &&     \
    apt-get install -y    \
        openjdk-8-jdk     \
        openssh-server    \
        curl

RUN curl -fSL https://dist.apache.org/repos/dist/release/hadoop/common/KEYS -o /tmp/hadoop_keys && \
    gpg --import /tmp/hadoop_keys

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
ENV HADOOP_VERSION 2.8.0
ENV HADOOP_URL https://www.apache.org/dist/hadoop/common/hadoop-$HADOOP_VERSION/hadoop-$HADOOP_VERSION.tar.gz
RUN set -x \
    && curl -fSL "$HADOOP_URL" -o /tmp/hadoop.tar.gz \
    && curl -fSL "$HADOOP_URL.asc" -o /tmp/hadoop.tar.gz.asc \
    && gpg --verify /tmp/hadoop.tar.gz.asc \
    && tar -xvf /tmp/hadoop.tar.gz -C /opt/ \
    && rm /tmp/hadoop.tar.gz*

RUN ln -s /opt/hadoop-$HADOOP_VERSION/etc/hadoop /etc/hadoop && \
    cp /etc/hadoop/mapred-site.xml.template /etc/hadoop/mapred-site.xml && \
    mkdir /opt/hadoop-$HADOOP_VERSION/logs && \
    mkdir /hadoop-data

ENV HADOOP_PREFIX=/opt/hadoop-$HADOOP_VERSION
ENV HADOOP_CONF_DIR=/etc/hadoop
ENV MULTIHOMED_NETWORK=1

ENV USER=root
ENV PATH $HADOOP_PREFIX/bin/:$PATH

ADD entrypoint.sh /entrypoint.sh
RUN chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
