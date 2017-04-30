FROM sangwonl/hadoop-base:2.7.1
MAINTAINER Sangwon Lee <gamzabaw@gmail.com>

HEALTHCHECK CMD curl -f http://localhost:50075/ || exit 1

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop/dfs/data
RUN mkdir -p /hadoop/dfs/data
VOLUME /hadoop/dfs/data

ADD run.sh /run.sh
RUN chmod a+x /run.sh

# Web
EXPOSE 50075
# Default
EXPOSE 50010
# IPC
EXPOSE 50020

CMD ["/run.sh"]
