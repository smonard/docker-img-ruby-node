FROM fedora

# Install elementary libs
RUN dnf update -y
RUN dnf groupinstall -y "Development Tools"
RUN dnf install -y which wget libffi-devel readline-devel sqlite-devel zlib-devel openssl-devel
RUN dnf remove ruby -y

# Install Ruby
RUN wget https://cache.ruby-lang.org/pub/ruby/3.1/ruby-3.1.2.tar.gz
RUN tar -xf ruby-3.1.2.tar.gz
WORKDIR ruby-3.1.2
RUN ./configure
RUN make
RUN make install
RUN gem install bundler
WORKDIR /
RUN rm -rf ruby-3.1.2.tar.gz ruby-3.1.2

# Install Node
RUN curl -sL https://rpm.nodesource.com/setup_18.x |  bash -
RUN dnf install -y nodejs

# Install SQLite3
RUN wget https://www.sqlite.org/2022/sqlite-autoconf-3390100.tar.gz
RUN tar -xf sqlite-autoconf-3390100.tar.gz
WORKDIR sqlite-autoconf-3390100
RUN ./configure
RUN make
RUN make install
WORKDIR /
RUN rm -rf sqlite-autoconf-3390100.tar.gz sqlite-autoconf-3390100
WORKDIR /main

CMD [ "cat /etc/os-release && uname -a && ruby --version && bundler --version && echo Node-env: && node --version && npm --version" ]
ENTRYPOINT [ "/bin/sh", "-c" ]