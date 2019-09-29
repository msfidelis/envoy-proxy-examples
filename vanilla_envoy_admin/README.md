

## Enable Admin Metrics

```
docker build -t envoy_vanilla_admin .
```

```
docker run -it -p 8080:8080 -p 9901:9901 envoy_vanilla_admin
```

## Example Requests

```
curl http://0.0.0.0:9901/help
curl http://0.0.0.0:9901/clusters
curl http://0.0.0.0:9901/listeners
curl http://0.0.0.0:9901/logging -X POST
curl http://0.0.0.0:9901/stats
curl http://0.0.0.0:9901/stats/prometheus
```