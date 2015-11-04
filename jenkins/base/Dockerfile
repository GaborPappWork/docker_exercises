FROM jre_base

ENV JENKINS_VERSION 1.625.1
ENV JENKINS_HOME /var/jenkins_home
ENV JENKINS_SLAVE_AGENT_PORT 5000

RUN useradd -d "$JENKINS_HOME" -u 1000 -m -s /bin/bash jenkins
RUN cd /opt && wget http://mirrors.jenkins-ci.org/war-stable/$JENKINS_VERSION/jenkins.war
RUN chown -R jenkins "$JENKINS_HOME"

VOLUME /var/jenkins_home

EXPOSE 8080
EXPOSE 5000

USER jenkins

ENTRYPOINT ["/tini", "--", "java", "-jar", "/opt/jenkins.war"]
