# es_state_query
elasticsearch local for query verification

# Handy commands

## spinup using docker
`docker network create somenetwork`

`docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:<tag>`

`curl -v localhost:9200`

## All indexed fields
`curl -v localhost:9200/test_index/_mapping`

## simple query
`curl -v localhost:9200/test_index/_search?q=accountId%3ABIP02100400&size=100`

## Experimentation commands
`curl -X DELETE -H "Content-Type: application/json" --data "@/Users/arun/Documents/es_state.json" http://localhost:9200/test_index`

`curl -X PUT -H "Content-Type: application/json" --data "@/Users/arun/Documents/es_state.json" http://localhost:9200/test_index`

`curl -X POST -H "Content-Type: application/json" --data "{\"streetAddress\":{\"state\":\"Victoria\"}}" http://localhost:9200/test_index/_doc/`

`curl -H "Content-Type: application/json" --data "{\"query\":{\"term\":{\"streetAddress.state\":\"victoria\"}}}" localhost:9200/test_index/_search | json_pp`

`curl -H "Content-Type: application/json" --data "@/Users/arun/projects/elasticsearch-indexes/query_state_vic.json" localhost:9200/test_index/_search | json_pp`
