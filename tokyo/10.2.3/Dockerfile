FROM ubuntu:16.04

ENV NUMBER_VERSION=19
ENV NAME_VERSION=tokyo
ENV SEMANTIC_VERSION=10.2.3

RUN apt-get -y update \
    && apt-get -y install \
    vim \
    wget \
    curl \
    unzip \
    build-essential \
    zlib1g-dev \
    libcurl3 \
    libcurl4-gnutls-dev \
    xterm \
    && apt-get -y autoremove \
    && apt-get -y autoclean
RUN wget https://github.com/HashLoad/delphi-dev/releases/download/${NAME_VERSION}/paserver_${NUMBER_VERSION}.tar.gz \
    && tar -xzvf paserver_$NUMBER_VERSION.tar.gz \
    && rm paserver_$NUMBER_VERSION.tar.gz
RUN echo "INTERBASE=/opt/interbase" >> /etc/environment \
    && wget -P $INTERBASE/lib https://github.com/HashLoad/delphi-dev/releases/download/${NAME_VERSION}/libgds.so \
    && chmod 755 $INTERBASE/lib/libgds.so \
    && cp $INTERBASE/lib/libgds.so /usr/lib/
RUN wget https://github.com/HashLoad/delphi-dev/releases/download/${NAME_VERSION}/LinuxEMSServer.tar \
    https://github.com/HashLoad/delphi-dev/releases/download/${NAME_VERSION}/ems_install.sh \
    && chmod +x ./ems_install.sh \
    && ./ems_install.sh \
    && rm LinuxEMSServer.tar ems_install.sh

WORKDIR /paserver

EXPOSE 64211

CMD ["./paserver", "-password="]