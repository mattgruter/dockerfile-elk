FROM java:7-jre
MAINTAINER Matthias Grüter <matthias@grueter.name>

# To update, check http://www.elasticsearch.org/overview/elkdownloads/
ENV LOGSTASH_VERSION 1.4.2
ENV LOGSTASH_SHA1 d59ef579c7614c5df9bd69cfdce20ed371f728ff

RUN echo $LOGSTASH_SHA1  logstash.tar.gz > logstash.tar.gz.sha1 && \
    curl -L -o logstash.tar.gz https://download.elasticsearch.org/logstash/logstash/logstash-${LOGSTASH_VERSION}.tar.gz && \
    sha1sum -c --quiet logstash.tar.gz.sha1 && \
    tar xzf logstash.tar.gz && \
    mv logstash-${LOGSTASH_VERSION} logstash && \
    rm logstash.tar.gz*

WORKDIR /logstash
EXPOSE 514
EXPOSE 4560
COPY logstash.conf /logstash/logstash.conf

CMD ["bin/logstash", "-f", "logstash.conf"]
