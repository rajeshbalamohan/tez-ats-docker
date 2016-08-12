FROM centos

RUN yum install -y git npm wget gettext sudo graphviz

WORKDIR /usr/local
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz
RUN tar -zxf jdk-8u102-linux-x64.tar.gz
ENV JAVA_HOME /usr/local/jdk1.8.0_102

RUN wget http://www-us.apache.org/dist/zeppelin/zeppelin-0.6.0/zeppelin-0.6.0-bin-all.tgz
RUN tar -zxf zeppelin-0.6.0-bin-all.tgz
RUN ln -s /usr/local/zeppelin-0.6.0-bin-all /usr/local/zeppelin

RUN rm -rf /usr/local/zeppelin/conf

COPY lib/*.jar /usr/local/zeppelin/interpreter/spark/dep/
RUN rm -rf /usr/local/zeppelin/bin/zeppelin.sh
RUN rm -rf /usr/local/zeppelin/logs/
COPY zeppelin.sh /usr/local/zeppelin/bin/zeppelin.sh

ENV ZEPPELIN_SPARK_MAXRESULT=10000
ENV ZEPPELIN_JAVA_OPTS=" -Djava.util.Arrays.useLegacyMergeSort=true -Dspark.executor.memory=2g -Dspark.cores.max=2  "
ENV ZEPPELIN_SPARK_MASTER="local[*]"
ENV ZEPPELIN_SPARK_DRIVER_MEMORY="512M"

EXPOSE 11000
WORKDIR /usr/local/zeppelin/
ENTRYPOINT ["/usr/local/zeppelin/bin/zeppelin.sh"]
