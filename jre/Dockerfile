FROM tini_base

ENV VERSION 8
ENV UPDATE 74
ENV BUILD 02

RUN apt-get install -y wget && cd /opt && \
    wget --no-cookies --no-check-certificate \
         --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" \
         "http://download.oracle.com/otn-pub/java/jdk/${VERSION}u${UPDATE}-b${BUILD}/server-jre-${VERSION}u${UPDATE}-linux-x64.tar.gz" && \
    tar xzf server-jre-${VERSION}u${UPDATE}-linux-x64.tar.gz && \
    cd jdk1.${VERSION}.0_${UPDATE} && \
    update-alternatives --install /usr/bin/java java /opt/jdk1.${VERSION}.0_${UPDATE}/bin/java 2 && \
    update-alternatives --install /usr/bin/jar jar /opt/jdk1.${VERSION}.0_${UPDATE}/bin/jar 2 && \
    update-alternatives --install /usr/bin/javac javac /opt/jdk1.${VERSION}.0_${UPDATE}/bin/javac 2 && \
    update-alternatives --set jar /opt/jdk1.${VERSION}.0_${UPDATE}/bin/jar && \
    update-alternatives --set javac /opt/jdk1.${VERSION}.0_${UPDATE}/bin/javac && \
    rm -rf /opt/server-jre-${VERSION}u${UPDATE}-linux-x64.tar.gz

ENV JAVA_HOME /opt/jdk1.${VERSION}.0_${UPDATE}
ENV JRE_HOME ${JAVA_HOME}/jre
ENV PATH $PATH:$JAVA_HOME/bin:$JRE_HOME/bin

ENTRYPOINT ["/tini", "-s", "--", "java"  ]

CMD [ "-version" ]
