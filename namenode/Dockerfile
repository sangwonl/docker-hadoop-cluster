FROM sangwonl/hadoop-base:2.7.1
MAINTAINER Sangwon Lee <gamzabaw@gmail.com>

HEALTHCHECK CMD curl -f http://localhost:50070/ || exit 1

ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
RUN mkdir -p /hadoop/dfs/name
VOLUME /hadoop/dfs/name

ADD run.sh /run.sh
RUN chmod a+x /run.sh

# Web
EXPOSE 50070
# Default
EXPOSE 8020

CMD ["/run.sh"]
