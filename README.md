# Docker images for the ELK stack

Run the [ELK stack](http://www.elasticsearch.org/overview/elkdownloads/), the end-to-end search and analytics platform.

(ELK stands for [Elasticsearch](http://www.elasticsearch.org/overview/elasticsearch), [Logstash](http://www.elasticsearch.org/overview/logstash) and [Kibana](http://www.elasticsearch.org/overview/kibana))

Images on the Docker Hub:

- Elasticsearch: [elasticsearch](https://registry.hub.docker.com/u/library/elasticsearch/)
- Logstash: [mattgruter/logstash](https://registry.hub.docker.com/u/mattgruter/logstash/)
- Kibana: [mattgruter/kibana](https://registry.hub.docker.com/u/mattgruter/kibana/)

## Getting started
To run the ELK stack do:

    docker run -d --name es elasticsearch
    docker run -d --link es:elasticsearch -p 4560:4560 mattgruter/logstash
    docker run -d --link es:elasticsearch -p 8080:8080 mattgruter/kibana

Now point your browser at [http://localhost:8080](http://localhost:8080) and send data to `tcp://localhost:4560`.


## Fig
If you use [fig](http://www.fig.sh/) you can bulid and start all containers with:

    fig up

Or if you don't want to build the images yourself and use the prebuild images from the Docker Hub:

    fig -f fig.prod.yml

And point your browser at [http://localhost:8080](http://localhost:8080) and send data to `tcp://localhost:4560`.

