FROM debian:jessie
MAINTAINER Matthias Grüter <matthias@grueter.name>

# To update, check http://www.elasticsearch.org/overview/kibana/installation/
ENV KIBANA_VERSION 4.0.0-rc1
ENV KIBANA_SHA1 b46154902ae37b21e4394fa3e0136af425294020

ADD https://download.elasticsearch.org/kibana/kibana/kibana-${KIBANA_VERSION}-linux-x64.tar.gz /kibana.tar.gz

RUN echo $KIBANA_SHA1  kibana.tar.gz > kibana.tar.gz.sha1 && \
    sha1sum -c --quiet kibana.tar.gz.sha1 && \
    tar xzf kibana.tar.gz && \
    mv kibana-${KIBANA_VERSION}-linux-x64 /kibana && \
    rm kibana.tar.gz*
    
WORKDIR /kibana
EXPOSE 8080
COPY kibana.yml /kibana/config/kibana.yml
COPY run.sh /kibana/run.sh

CMD ["./run.sh"]
