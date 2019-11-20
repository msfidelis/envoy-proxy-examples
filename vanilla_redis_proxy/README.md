## Redis Proxy

### Configure multi hosts on envoy 

```
docker-compose build
docker-compose up --force-recreate
```

```
docker-compose up
```


```
curl http://0.0.0.0:8080/version
```

## Test Service Load Balancing

``` bash
while true; do curl localhost:8080/version; echo; done;

# ---
{"version":1,"node_version":"8.6.0"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
```