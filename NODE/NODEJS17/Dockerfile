FROM        --platform=linux/amd64 node:17-bullseye-slim

LABEL       author="Robert Jansen" maintainer="rjansengd@gmail.com"

RUN         apt update \
            && apt -y install ffmpeg openjdk-17-jdk maven gradle openjdk-11-jdk iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
            && npm -g install npm@latest \
            && useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
