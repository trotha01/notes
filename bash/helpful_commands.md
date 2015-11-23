# Loop until it works
```bash
function force() {
  while [ $? -ne 0 ]; do $@; done
}
```

# Add-Hok http sink
echo -e "HTTP/1.1 200 OK\n\n $(date)" | nc -l 9090
