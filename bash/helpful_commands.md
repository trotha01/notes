# Loop until it works
```bash
function force() {
  while [ $? -ne 0 ]; do $@; done
}
```
