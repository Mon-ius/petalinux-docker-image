FROM ubuntu:18.04

ARG VERSION=2018.3
ARG FILE=petalinux-v2018.3-final-installer.run

#init files
ADD accept-eula.sh /
ADD sdk/${VERSION} /tmp/petalinux

RUN cat /tmp/petalinux/tpeta201803.gz* | zcat > /${FILE} \
    && rm -rf /tmp/petalinux/

#install dependences:
RUN dpkg --add-architecture i386 && apt-get update 

RUN export DEBIAN_FRONTEND=noninteractive \
    &&  apt-get install -y tzdata \ 
    &&  ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime \
    &&  dpkg-reconfigure --frontend noninteractive tzdata \
    && apt-get install -y \
    python \
    python3 \
    make \
    zlib1g-dev \ 
    tar \
    xinetd \
    build-essential \
    gcc \
    sudo \
    tofrodos \
    iproute2 \
    gawk \
    net-tools \
    expect \
    libncurses5-dev \
    tftpd \
    libssl-dev \
    flex \
    bison \
    libselinux1 \
    gnupg \
    wget \
    socat \
    gcc-multilib \
    libsdl1.2-dev \
    libglib2.0-dev \
    lib32z1-dev \
    zlib1g:i386 \
    libgtk2.0-0 \
    screen \
    pax \
    diffstat \
    xvfb \
    xterm \
    texinfo \
    gzip \
    unzip \
    cpio \
    chrpath \
    autoconf \
    lsb-release \
    libtool \
    libtool-bin \
    kmod \
    locales \
    rsync \
    git

RUN locale-gen en_US.UTF-8 && update-locale

#make a Vivado user
RUN adduser --disabled-password --gecos '' vivado \
    && usermod -aG sudo vivado \
    && echo "vivado ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Install bash4.3 to fit wired vivado software && Replace the bash
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils
RUN wget http://archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-14ubuntu1_amd64.deb  \
    && sudo apt-get install ./bash_4.3-14ubuntu1_amd64.deb -y --allow-downgrades \
    && rm ./bash_4.3-14ubuntu1_amd64.deb \
    && sudo rm /bin/sh \
    && sudo ln -s /bin/bash /bin/sh

# run the install
RUN chmod a+x /${FILE}  \
    && mkdir -p /opt/Xilinx/Petalinux/  \
    && chmod 777 /tmp /opt/Xilinx/Petalinux/  \
    && cd /tmp  \
    && sudo -u vivado /accept-eula.sh /${FILE} /opt/Xilinx/Petalinux/${VERSION}  \
    && rm -f /${FILE} /accept-eula.sh 

USER vivado
ENV HOME /home/vivado
ENV LANG en_US.UTF-8
RUN mkdir /home/vivado/project
WORKDIR /home/vivado/project

# add vivado tools to path, ignore the warning
RUN echo "source /opt/Xilinx/Petalinux/${VERSION}/settings.sh  > /dev/null 2>&1" >> /home/vivado/.bashrc

# add test bsp project
COPY bsp/xilinx-zc706-v2018.3-final.bsp /home/vivado/project/