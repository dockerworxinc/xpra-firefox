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

##

```
$ docker ps
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS   
           PORTS                              NAMES
2d313d89ce10        sassmann/debian-firefox   "firefox"                2 seconds ago       Up 1 seco
nd                                            fire
f1940aeabb09        jare/x11-bridge           "/usr/local/bin/run …"   About an hour ago   Up About 
an hour    22/tcp, 0.0.0.0:10000->10000/tcp   x11-bridge
```
