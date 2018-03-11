FROM dockerfile/ubuntu

RUN \
  apt-get update && \
  apt-get install -y firefox && \
  rm -rf /var/lib/apt/lists/*



# Create OpenSSH privilege separation directory
RUN mkdir /var/run/sshd 

RUN adduser --disabled-password --gecos "User" --uid 1000 user

# to allow adding the public key e.g. with docker exec -i x11-xpra /bin/bash -c 'cat > /home/user/.ssh/authorized_keys' < ~/.ssh/id_rsa.pub
RUN mkdir /home/user/.ssh/

VOLUME /home/user



CMD []
ENTRYPOINT ["/usr/bin/firefox"]
