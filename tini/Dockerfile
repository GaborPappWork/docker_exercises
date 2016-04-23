FROM ubuntu:trusty

ARG TINI_VERSION=0.9.0

ADD https://github.com/krallin/tini/releases/download/v${TINI_VERSION}/tini /tini
RUN chmod +x /tini

ENTRYPOINT ["/tini", "-s", "--"]
