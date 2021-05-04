# busybox-curl
* https://curl.se/download.html
* https://github.com/moparisthebest/static-curl/tags


usage
```
docker build -t busybox-curl:<tag> --build-arg --build-arg ARC=<OS Arch> --build-arg VER=<Curl Version>
```

example
```
docker build -t kkuroo/busybox-curl:7.76
```

example with arguments
```
docker build -t kkuroo/busybox-curl:v7.76.0 --build-arg ARC=amd64 --build-arg VER=v7.76.0 .
```
