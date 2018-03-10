# xpra-firefox

Firefox running inside 2 separate Docker containers

```
docker run -d \
 --name x11-bridge \
 -e MODE="tcp" \
 -e XPRA_HTML="yes" \
 -e DISPLAY=:14 \
 -e XPRA_PASSWORD=111 \
 -p 10000:10000 \
 jare/x11-bridge

docker run -d \
--name fire \
--volumes-from x11-bridge \
-e DISPLAY=:14  \
sassmann/debian-firefox firefox
```

##

```
curl http://localhost:10000/index.html?encoding=png&password=111
```
