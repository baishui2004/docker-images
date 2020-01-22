FROM openjdk:8-jre
MAINTAINER bs2004 <bs2004@163.com>

ENV KETTLE_HOME=/data-integration MYSQL_DRIVER_VERSION=5.1.42 PDI_USER=pentaho

RUN apt-get update
RUN apt-get install -y libwebkitgtk-1.0-0

RUN apt-get clean \
    && rm -rf /var/lib/apt/lists/* \
    && useradd -md $KETTLE_HOME -s /bin/bash $PDI_USER


RUN wget --progress=dot:giga http://downloads.sourceforge.net/project/pentaho/Pentaho%208.0/client-tools/pdi-ce-8.0.0.0-28.zip \
        && unzip -q *.zip \
        && rm -f *.zip

WORKDIR $KETTLE_HOME

RUN wget http://central.maven.org/maven2/mysql/mysql-connector-java/${MYSQL_DRIVER_VERSION}/mysql-connector-java-${MYSQL_DRIVER_VERSION}.jar \
        && rm -f lib/mysql*.jar \
        && mv *.jar lib/.

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai \
    && echo Asia/Shanghai > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata
