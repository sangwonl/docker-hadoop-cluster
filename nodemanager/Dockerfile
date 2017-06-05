FROM sangwonl/hadoop-base:latest
MAINTAINER Sangwon Lee <gamzabaw@gmail.com>

RUN apt-get install -y python

RUN pip3 install --upgrade \
    pip                    \
    matplotlib             \
    plotly                 \
    pandas                 \
    numpy                  \
    pymysql                \
    sqlalchemy             \
    boto                   \
    tensorflow             \
    scipy                  \
    scikit-learn           \
    statsmodels            \
    sympy

HEALTHCHECK CMD curl -f http://localhost:8042/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 8042

CMD ["/run.sh"]
