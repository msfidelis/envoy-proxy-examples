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
while true; do curl localhost:9090/healthcheck/fault; echo; done;

// ---

{"status":503,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":503,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":503,"description":"fault injection"}
```

## Test the same service behind front proxy with retry policy

``` bash
while true; do curl localhost:8080/healthcheck/fault; echo; done;

// ---

{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
{"status":200,"description":"fault injection"}
```