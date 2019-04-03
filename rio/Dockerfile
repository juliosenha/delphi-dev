FROM ubuntu:16.04

ENV VERSION_NUMBER=20
ENV VERSION_NAME=rio

RUN apt-get -y update \
    && apt-get -y install \
    curl \
    unzip \
    build-essential \
    zlib1g-dev \
    libcurl3 \
    libcurl4-gnutls-dev \
    xterm \
    && apt-get -y autoremove \
    && apt-get -y autoclean
RUN wget https://github.com/HashLoad/delphi-dev/releases/download/${VERSION_NAME}/paserver_19.tar.gz\
    && tar -xzvf paserver_${VERSION_NUMBER}.tar.gz
RUN wget https://github.com/HashLoad/delphi-dev/releases/download/${VERSION_NAME}/LinuxEMSServer.tar . \ 
    && wget https://github.com/HashLoad/delphi-dev/releases/download/${VERSION_NAME}/ems_install.sh . \
    && ./ems_install.sh

WORKDIR /paserver

EXPOSE 64211

CMD ["./paserver", "-password="]