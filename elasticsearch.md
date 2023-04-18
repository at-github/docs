# Elasticsearch

## Some resources
- https://grafikart.fr/tutoriels/elastic-search-626
- https://www.elastic.co/fr/elasticsearch/
- https://github.com/mobz/elasticsearch-head

## Install
[Link](https://www.linuxcapable.com/how-to-install-elasticsearch-on-debian-11-bullseye/)

## Glossary

| Term     | Explanation       |
| -------- | -----------       |
| Index    | Like a database   |
| Typew    | Like a table      |
| Document | Like a row        |
| Hits     | Result & Metadata |
| Shards   | Workers           |

## Some basic request

Below the index is named *samples*

### Delete index
```shell
curl -X DELETE 'http://localhost:9200/samples'
```

### List all indexes
```shell
curl -X GET 'http://localhost:9200/_cat/indices?v'`
```

### List all docs in index
```shell
curl -X GET 'http://localhost:9200/sample/_search'`
```

### Query using URL parameters
```shell
curl -X GET http://localhost:9200/samples/_search?q=school:Harvard`
```

### Query with JSON aka Elasticsearch Query DSL:
```shell
curl -XGET --header 'Content-Type: application/json' http://localhost:9200/samples/_search -d '{
  "query" : {
    "match" : { "school": "Harvard" }
  }
}'
```

### List index mapping
```shell
curl -X GET http://localhost:9200/samples`
```

### Add data:
```shell
curl -XPUT --header 'Content-Type: application/json' http://localhost:9200/samples/_doc/1 -d '{
   "school" : "Harvard"			
}'
```

### Update doc:
```shell
curl -XPUT --header 'Content-Type: application/json' http://localhost:9200/samples/_doc/2 -d '
{
    "school": "Clemson"
}'

curl -XPOST --header 'Content-Type: application/json' http://localhost:9200/samples/_doc/2/_update -d '{
  "doc" : {
    "students": 50000
  }
}'
```

### Backup index:
```shell
curl -XPOST --header 'Content-Type: application/json' http://localhost:9200/_reindex -d '{
  "source": {
    "index": "samples"
  },
  "dest": {
    "index": "samples_backup"
  }
}'
```

### Bulk load data in JSON format:
```shell
export pwd="elastic:"

curl --user $pwd  -H 'Content-Type: application/x-ndjson' -XPOST 'https://58571402f5464923883e7be42a037917.eu-central-1.aws.cloud.es.io:9243/0/_bulk?pretty' --data-binary @<file>
```

### Show cluster health:
```shell
curl --user $pwd  -H 'Content-Type: application/json' -XGET https://58571402f5464923883e7be42a037917.eu-central-1.aws.cloud.es.io:9243/_cluster/health?pretty
```

### Aggregation and Bucket Aggregation:
```shell
curl -XGET --user $pwd --header 'Content-Type: application/json'  https://58571402f5464923883e7be42a037917.eu-central-1.aws.cloud.es.io:9243/logstash/_search?pretty -d '{
  "aggs": {
    "cityName": {
      "terms": {
        "field": "geoip.city_name.keyword",
          "size": 50

      }
    }
  }
}
'
```

### Pretty Print
` curl -X GET 'http://localhost:9200/(index)/_search'?pretty=true`

### To query and return only certain fields:
```shell
GET filebeat-7.6.2-2020.05.05-000001/_search
{
  "_source": ["suricata.eve.timestamp","source.geo.region_name","event.created"],
  "query":      {
    "match" : { "source.geo.country_iso_code": "GR" }
  }
}
```

### To Query by Date:
```shell
GET filebeat-7.6.2-2020.05.05-000001/_search
{
  "query": {
    "range" : {
      "event.created": {
        "gte" : "now-7d/d"
      }
    }
  }
}
```
