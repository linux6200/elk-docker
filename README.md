# elk-docker
the ELK in Docker


# About

Elasticsearch 6 with x-pack plugin installed.
Based on alpine linux for minimal size.

# Build
docker build -t guozb/elasticsearch-x-pack . --file Dockerfile_elasticsearch-x-pack
docker build -t guozb/kibana-x-pack . --file Dockerfile_kibana-x-pack

# Usage

Before you start this container make sure
to set the max_map_count on your docker host.

```bash
sudo sysctl vm.max_map_count=262144
```

Start the elasticsearch container

```bash
docker run --name es-xpack -p9200:9200 -p9300:9300 -d guozb/elasticsearch-x-pack
```

Optional start kibana x-pack
```bash
docker run -p 5601:5601 --link es-xpack:elasticsearch --name kb-xpack -d guozb/kibana-x-pack
```
login with
user: elastic
pass: changeme
