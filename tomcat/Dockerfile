FROM jre_base

ARG MAIN_VERSION=8
ARG SUB_VERSION=0.33
ENV CATALINA_HOME /opt/tomcat
ENV CATALINA_OPTS "-Xms256m -Xmx1024m -XX:MaxPermSize=256m"

RUN cd /opt && \
	wget http://www.apache.org/dist/tomcat/tomcat-$MAIN_VERSION/v$MAIN_VERSION.$SUB_VERSION/bin/apache-tomcat-$MAIN_VERSION.$SUB_VERSION.tar.gz -O tomcat.tar.gz && \
	tar -xvf tomcat.tar.gz && \
	rm tomcat.tar.gz && \
	mv /opt/apache-tomcat-$MAIN_VERSION.$SUB_VERSION /opt/tomcat

RUN useradd -u 1000 -m -s /bin/bash tomcat && chown -R tomcat "$CATALINA_HOME" 

EXPOSE 8080

USER tomcat

ENTRYPOINT [ "/tini", "-s", "--", "/opt/tomcat/bin/catalina.sh" ]

CMD [ "run" ]
