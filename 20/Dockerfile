FROM ubuntu:16.04

ENV VERSION=20

COPY paserver_$VERSION.tar.gz .

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
RUN tar -xzvf paserver_$VERSION.tar.gz

WORKDIR /paserver

EXPOSE 64211

CMD ["./paserver", "-password="]
