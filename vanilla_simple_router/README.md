

## Simple Proxy to Google

```
docker build -t envoy_vanilla .
```

```
docker run -it -p 8080:8080 envoy_vanilla
```

```
curl http://0.0.0.0:8080
```