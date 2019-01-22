# oldelk
kibana 4.1.11 &lt;= elasticsearch 1.7 &lt;= logstash 2.4.1 &lt;= fakelog filebeat 6.5.4

Some Dockerfile code come from github about elasticsearch & lotstash etc...

## elasticsearch mapping geo_point

1. template must have
2. \_default\_ for all index
3. geohash is options

````
curl -v -XGET elasticsearch:9200/_template
curl -v -XPUT elasticsearch:9200/_template/template_filebeat -H 'Content-Type: application/json' -d'
{
  "template": "filebeat*",
  "settings": {
    "number_of_shards": 1
  },
  "mappings": {
    "_default_": {
        "properties" : {
            "filebeatserveripgeoip.location": {
                "type": "geo_point",
                "geohash": true
            }
        }
    }
  }
  
}'

curl -v -XGET elasticsearch:9200/_cat/indices?v
curl -v -XDELETE elasticsearch:9200/filebeat-6.5.4-oooxxx
```
