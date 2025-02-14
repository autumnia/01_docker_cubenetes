# Logstash

docker run -d --name logstash -p 5044:5044 -p 9600:9600 -v ./logstash.conf:/usr/share/logstash/pipeline/logstash.conf docker.elastic.co/logstash/logstash:8.10.0


docker network create elastic-network
docker network connect elastic-network elasticsearch
docker network connect elastic-network logstash