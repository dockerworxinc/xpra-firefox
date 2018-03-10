# Running Xpra and Firefox as microservices

## Pre-requisite:

- Install Docker
- Install Docker Compose

## Clone the Repository

```
git clone https://github.com/dockerworxinc/xpra-firefox
cd xpra-firefox
```

## Running Docker Compose

```
docker-compose up 
```

You must see both the container up and running as shown below:

```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                              N
AMES
d9d5bec63dc6        fedora/firefox      "vncserver -fg"          4 minutes ago       Up 4 minutes        5901/tcp                           f
irefox
5250c7f6d21d        jare/x11-bridge     "/usr/local/bin/run …"   4 minutes ago       Up 4 minutes        22/tcp, 0.0.0.0:10000->10000/tcp   x
11-bridge
```

Method-2:

# Running it without Docker Compose

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
fedora/firefox 
```

##

```
curl http://localhost:10000/index.html?encoding=png&password=111
```

