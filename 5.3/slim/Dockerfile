FROM debian:jessie
MAINTAINER Nicholas Iaquinto <nickiaq@gmail.com>

ENV LUA_HASH 33278c2ab5ee3c1a875be8d55c1ca2a1
ENV LUA_MAJOR_VERSION 5.3
ENV LUA_MINOR_VERSION 2
ENV LUA_VERSION ${LUA_MAJOR_VERSION}.${LUA_MINOR_VERSION}

RUN apt-get update && \
    apt-get install -y build-essential curl libreadline-dev && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir /usr/src/lua && \
    cd /usr/src/lua && \
    curl -fSLO http://www.lua.org/ftp/lua-${LUA_VERSION}.tar.gz && \
    echo "${LUA_HASH}  lua-${LUA_VERSION}.tar.gz" | md5sum -c - && \
    tar zxf lua-${LUA_VERSION}.tar.gz && \
    make -C lua-${LUA_VERSION} linux test && \
    make -C lua-${LUA_VERSION} install && \
    rm -rf *.tar.gz lua-${LUA_VERSION} && \
    apt-get purge -y --auto-remove build-essential curl libreadline-dev

CMD ["/usr/local/bin/lua"]
