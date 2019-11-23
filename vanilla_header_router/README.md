## Routing by header

```
docker-compose build
docker-compose up --force-recreate
```

## Header configuration

```yml
    # Header based route example
    - match:
        prefix: "/version"
        headers:
        - name: "x-api-version"
            exact_match: "1"
    route:
        cluster: cluster_version_1
    # ----

    # Header based route example
    - match:
        prefix: "/version"
        headers:
        - name: "x-api-version"
            exact_match: "2"
    route:
        cluster: cluster_version_2
    # ----
```

### Using version 1

```bash
curl -H "x-api-version: 1" localhost:8080/version -i


HTTP/1.1 200 OK
content-type: application/json; charset=utf-8
cache-control: no-cache
content-length: 36
accept-ranges: bytes
date: Sat, 23 Nov 2019 22:16:50 GMT
x-envoy-upstream-service-time: 1
server: envoy

{"version":1,"node_version":"8.6.0"}

```


### Using version 2

```bash
curl -H "x-api-version: 2" localhost:8080/version -i

HTTP/1.1 200 OK
content-type: application/json; charset=utf-8
cache-control: no-cache
content-length: 37
accept-ranges: bytes
date: Sat, 23 Nov 2019 22:18:38 GMT
x-envoy-upstream-service-time: 2
server: envoy

{"version":2,"node_version":"12.8.1"}
```