## HTTP retry

```
docker-compose build
docker-compose up --force-recreate
```

```
docker-compose up
```

```
curl http://0.0.0.0:8080/random/500
```

## Test Service Directly

``` bash
while true; do curl localhost:9090/random/500; echo; done;

// ---

{"code":500,"message":"Internal Server Error"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":500,"message":"Internal Server Error"}
{"code":500,"message":"Internal Server Error"}
{"code":200,"message":"Success"}
{"code":500,"message":"Internal Server Error"}
{"code":200,"message":"Success"}
{"code":500,"message":"Internal Server Error"}
{"code":500,"message":"Internal Server Error"}
```

## Test the same service behind front proxy with retry policy

``` bash
while true; do curl localhost:8080/random/500; echo; done;

// ---

{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
{"code":200,"message":"Success"}
```