FROM centos

# Install elementary libs
RUN yum groupinstall -y "Development Tools"
RUN yum install -y which wget libffi-devel ruby readline-devel sqlite-devel zlib-devel openssl-devel

# Install Ruby
RUN wget https://cache.ruby-lang.org/pub/ruby/3.0/ruby-3.0.0.tar.gz
RUN tar -xf ruby-3.0.0.tar.gz
WORKDIR ruby-3.0.0
RUN ./configure --prefix=/usr
RUN make
RUN make install
RUN gem install bundler
WORKDIR /
RUN rm -rf ruby-3.0.0.tar.gz ruby-3.0.0

# Install Node
RUN curl -sL https://rpm.nodesource.com/setup_14.x |  bash -
RUN yum install -y nodejs

# Install SQLite3
RUN wget https://www.sqlite.org/2021/sqlite-autoconf-3340100.tar.gz
RUN tar -xf sqlite-autoconf-3340100.tar.gz
WORKDIR sqlite-autoconf-3340100
RUN ./configure --prefix=/usr
RUN make
RUN make install
WORKDIR /
RUN rm -rf sqlite-autoconf-3340100.tar.gz sqlite-autoconf-3340100
WORKDIR /main
