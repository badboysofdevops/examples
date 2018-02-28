FROM ubuntu:16.04

RUN apt-get update && apt-get install -y xterm \
    vim-gtk build-essential cmake wget && \
    apt-get install -y libnotify4 libnss3 libxkbfile1 libgconf-2-4 \
    libsecret-1-0 gconf2-common libnspr4 libnss3-nssdb libsecret-common \
    libxss1 git libasound2

RUN useradd -ms /bin/bash developer && \
    mkdir -p /etc/sudoers.d/ && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    cd /tmp && \
    wget -O code.deb https://go.microsoft.com/fwlink/?LinkID=760868 && \
    dpkg -i code.deb

USER developer
ENV HOME /home/developer
CMD /usr/bin/code -w

