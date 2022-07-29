FROM        --platform=linux/amd64 node:17-bullseye-slim

LABEL       author="Robert Jansen" maintainer="rjansengd@gmail.com"

RUN         apt update \
            && apt -y install sudo htop neofetch nano wget wine ffmpeg openjdk-17-jdk maven gradle openjdk-11-jdk iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool \
            && npm -g install npm@latest \
            && useradd -m -d /home/container container \
            && wget https://packages.microsoft.com/config/debian/11/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
            && sudo dpkg -i packages-microsoft-prod.deb \
            && rm packages-microsoft-prod.deb \
            && sudo apt-get update \
            && sudo apt-get install -y apt-transport-https \
            && sudo apt-get update \
            && sudo apt-get install -y dotnet-sdk-6.0 dotnet-runtime-6.0

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
COPY        ./max_user_watches /proc/sys/fs/inotify/max_user_watches
COPY        ./custom_promt.sh /etc/profile.d/custom_prompt.sh

CMD         [ "/bin/bash", "/entrypoint.sh" ]
