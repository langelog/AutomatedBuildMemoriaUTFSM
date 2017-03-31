FROM ubuntu:16.04
MAINTAINER Luis Gonzalez <langelog@me.com>

RUN apt-get update
RUN apt install -y zsh git rar unrar zip unzip
RUN apt install -y build-essential cmake libv4l-dev pkg-config libgtk2.0-dev \
                          libtiff5-dev libjasper-dev libavformat-dev libswscale-dev \
                          libavcodec-dev libjpeg8-dev python-dev python-numpy \
                          libtbb2 libtbb-dev libpng-dev libdc1394-22-dev

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer
    
RUN cd /home/developer && \
    wget -c https://root.cern.ch/download/root_v6.08.06.Linux-ubuntu16-x86_64-gcc5.4.tar.gz && \
    tar xvf root_v6.08.06.Linux-ubuntu16-x86_64-gcc5.4.tar.gz
    
USER developer
ENV HOME /home/developer
CMD /bin/bash
