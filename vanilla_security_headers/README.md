## Grant security headers 

# [Hardening Your HTTP Security Headers - KeyCDN](https://www.keycdn.com/blog/http-security-headers)

```
docker-compose build --no-cache
docker-compose up --force-recreate
```

## Add or remove headers

```yml
    response_headers_to_add:
        - header:
            key: x-xss-protection
            value: "1; mode=block"

        - header:
            key: strict-transport-security
            value: "max-age=31536000; includeSubDomains; preload"

        - header:
            key: x-frame-options
            value: "SAMEORIGIN"

        - header:
            key:  x-content-type-options
            value: "nosniff"

        - header:
            key:  feature-policy
            value: "autoplay 'none'; camera 'none'"

        - header:
            key:  x-content-type-options
            value: "nosniff"
```

```bash
curl  localhost:8080/version -i

HTTP/1.1 200 OK
content-type: application/json; charset=utf-8
cache-control: no-cache
content-length: 37
date: Sun, 24 Nov 2019 02:22:09 GMT
x-envoy-upstream-service-time: 1
x-xss-protection: 1; mode=block
strict-transport-security: max-age=31536000; includeSubDomains; preload
x-frame-options: SAMEORIGIN
x-content-type-options: nosniff
feature-policy: autoplay 'none'; camera 'none'
x-content-type-options: nosniff
server: envoy

{"version":2,"node_version":"12.8.1"}
```