FROM docker.elastic.co/elasticsearch/elasticsearch:5.4.1
LABEL maintainer "toyamarinyon <toyamarinyon@gmail.com>"

#USER root
#RUN ulimit -a 65536
#RUN echo 'elasticsearch  -  nofile  65536' >> /etc/security/limits.conf
#RUN mkdir -p /etc/systemd/system/elasticsearch.service.d && echo '[Service]\nLimitMEMLOCK=infinity' >> /etc/systemd/system/elasticsearch.service.d/elasticsearch.conf
#
#USER elasticsearch
ENV PLUGIN_LIST='analysis-kuromoji repository-gcs'\
    CLUSTER_NAME=elasticsearch-default\
    NODE_NAME=elasticsearch\
    NODE_MASTER=true\
    NODE_DATA=true\
    NODE_INGEST=true\
    HTTP_ENABLE=true\
    NETWORK_HOST=_site_\
    HTTP_CORS_ENABLE=true\
    HTTP_CORS_ALLOW_ORIGIN=*\
    NUMBER_OF_MASTERS=1\
    MAX_LOCAL_STORAGE_NODES=1\
    SHARD_ALLOCATION_AWARENESS=""\
    SHARD_ALLOCATION_AWARENESS_ATTR=""\
    DISCOVERY_SERVICE=elasticsearch-discovery\
    XPACK_SECURITY_ENABLED=false\
    XPACK_MONITARING_ENABLED=false\
    XPACK_ML_ENABLED=false\
    XPACK_GRAPH_ENABLED=false\
    XPACK_WATCHER_ENABLED=false

RUN for plugin in $PLUGIN_LIST; do elasticsearch-plugin install --batch "$plugin"; done

COPY config/elasticsearch.yml config/

