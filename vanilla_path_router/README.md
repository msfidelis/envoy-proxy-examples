## Proxy path routing

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

## Test Service Proxy

### Service on /whois

``` bash
curl http://localhost:8080/whois/google.com -i

# ---

HTTP/1.1 200 OK
server: envoy
content-type: application/json
content-length: 720
date: Sat, 16 Nov 2019 22:41:53 GMT
x-envoy-upstream-service-time: 65

{"domain":"google.com.br","owner":"Google Brasil Internet Ltda","ownerid":"06.990.590/0001-23","responsible":"Domain Administrator","country":"BR BR BR","ownerC":"DOADM17","adminC":"DOADM17","techC":"DOADM17","billingC":"NAB51","nserver":"ns1.google.com ns2.google.com ns3.google.com ns4.google.com","nsstat":"20191111 AA 20191111 AA 20191111 AA 20191111 AA","nslastaa":"20191111 20191111 20191111 20191111","created":"19990518 #162310 20100520 20020619","changed":"20190417 20180324 20181011","expires":"20200518","status":"published","nicHdlBr":"DOADM17 NAB51","person":"Domain Admin NameAction do Brasil","eMail":"ccops@markmonitor.com mail@nameaction.com","ofQueriesAre":"domain (.br), registrant (tax ID), ticket,"}
```

### Service on /faker

``` bash
curl http://localhost:8080/faker/male -i

# ---

HTTP/1.1 200 OK
content-type: application/json
content-length: 357
server: envoy
date: Sat, 16 Nov 2019 22:43:00 GMT
x-envoy-upstream-service-time: 34

{"address":"Campo de Costa\nCustodinha\n45257242 da Cruz da Praia / BA","blood_group":"AB-","company":"Carvalho","cpf":"125.046.387-44","job":"Catador de carangueijos","license_plate":"ZBM-8461","name":"Calebe Ara\u00fajo","residence":"Campo Lara Porto\nAntonio Ribeiro De Abreu 1\u00aa Se\u00e7\u00e3o\n87143-327 da Costa / MS","rg":"287316543","sex":"M"}
```
