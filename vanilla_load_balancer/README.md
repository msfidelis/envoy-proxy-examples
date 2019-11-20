## Load Balancer

### Configure multi hosts on envoy 

```yml
  clusters:
    - name: "cluster_example"
      connect_timeout: "1s"
      type: "strict_dns"
      lb_policy: "ROUND_ROBIN"
      hosts:

        - socket_address:
            address: "node_1"
            port_value: 8000

        - socket_address:
            address: "node_2"
            port_value: 8000
```

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