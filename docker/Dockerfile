FROM node:10

RUN npm install http-server -g

RUN apt-get update && apt-get install -y sudo vim wget zip unzip

RUN useradd -m -u 999 -o -s /bin/bash learner && \
    usermod -a -G node learner && \
    echo "learner ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/learner && \
    chmod 0400 /etc/sudoers.d/learner