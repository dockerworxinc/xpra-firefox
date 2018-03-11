# Running Xpra and Firefox on seperate container

```
docker run -p 2020:22 -d --name x11-xpra reto/x11-xpra 
```

## Copy your ssh public key

```
docker exec -i x11-xpra /bin/bash -c 'cat > /home/user/.ssh/authorized_keys' < ~/.ssh/id_rsa.pub
```

## Start xclock

```
ssh -p 2020 user@localhost xclock
```

The DISPLAY variable set to :100 which the virtual display provided by Xpra. You will not see the application until a client connects to the Xpra server.

To connect a client from the local machine

```
xpra --ssh="ssh -p 2020" attach ssh:user@localhost:100
```
