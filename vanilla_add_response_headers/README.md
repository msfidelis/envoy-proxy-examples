## Simple Header manipulation on Envoy

```
docker-compose build --no-cache
docker-compose up --force-recreate
```

## Add or remove headers

```yml
    route_config:
    name: local_route

    # How to add headers
    response_headers_to_add:
        - header:
            key: x-this-is-a-custom-header
            value: "true"

    # How to remove headers
    response_headers_to_remove:
        - accept-ranges

    # ----
```


```bash
curl  localhost:8080/version -i

HTTP/1.1 200 OK
content-type: application/json; charset=utf-8
cache-control: no-cache
content-length: 37
date: Sat, 23 Nov 2019 22:58:33 GMT
x-envoy-upstream-service-time: 1
x-this-is-a-custom-header: true
server: envoy

{"version":2,"node_version":"12.8.1"}
```