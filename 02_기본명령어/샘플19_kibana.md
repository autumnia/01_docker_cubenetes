# kibana
docker run -d --name kibana -h kibana --network elastic-network -p 5601:5601 -e "ELASTICSEARCH_HOSTS=http://elasticsearch:9200" kibana:8.10.1

docker network connect elastic-network kibana