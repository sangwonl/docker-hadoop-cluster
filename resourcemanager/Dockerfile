FROM sangwonl/hadoop-base:2.7.1
MAINTAINER Sangwon Lee <gamzabaw@gmail.com>

HEALTHCHECK CMD curl -f http://localhost:8088/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 8088

CMD ["/run.sh"]
