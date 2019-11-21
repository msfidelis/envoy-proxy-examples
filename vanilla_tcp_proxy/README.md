

# Test TCP Connection status

```bash
echo 'ping' | nc 0.0.0.0 8080 -v
```

```bash
echo "SET $(date +%s) kkkkkk"  | nc 0.0.0.0 8080 -v
```

# Set a lot of keys on redis

```bash
while true; do echo "SET $(date +%s) kkkkkk"  | nc 0.0.0.0 8080 -v; echo; done;
```

