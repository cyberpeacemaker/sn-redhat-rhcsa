```shell
>FILE 2>&1
| tee
sed -n '5p' filename
```
- numbered channels (file descriptor), [stdin, stdout, stderr]
- pipeline, r