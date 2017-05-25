FROM tomcat:8.0-jre8

MAINTAINER "Jeff Liu<jeff.l.crazy@gmail.com>"

ADD certs $CATALINA_HOME/conf/certs
ADD tomcat-users.xml $CATALINA_HOME/conf/
ADD server.xml $CATALINA_HOME/conf/


EXPOSE 80 443
VOLUME [${CATALINA_HOME}"/conf/certs", $CATALINA_HOME"/webapps"]

CMD  ["catalina.sh", "jpda", "run"]
