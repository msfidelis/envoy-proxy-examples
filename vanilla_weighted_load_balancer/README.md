## Weighted Load Balancing 

```
docker-compose build
docker-compose up --force-recreate
```

## Weighting configuration

```yml
    # Weighted load balancing example
    - match:
        prefix: "/version"
    route:
        weighted_clusters:
        clusters:
        - name: cluster_version_1
            weight: 10
        - name: cluster_version_2
            weight: 90
    # ----
```

### Balance testing

```bash
while true; do curl localhost:8080/version; echo; sleep 1;  done


{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
{"version":1,"node_version":"8.6.0"}
{"version":2,"node_version":"12.8.1"}
{"version":2,"node_version":"12.8.1"}
```