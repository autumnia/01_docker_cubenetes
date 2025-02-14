# Elastic Search

## docker 실행
docker run -d --name elasticsearch -p 9200:9200 -e "discovery.type=single-node" -e "xpack.security.enabled=false" -e "xpack.security.http.ssl.enabled=false" docker.elastic.co/elasticsearch/elasticsearch:8.10.0

## 실행 후 접속 주소
http://localhost:9200/_cat/indices