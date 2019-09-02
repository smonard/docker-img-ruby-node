FROM centos

# Install elementary libs
RUN yum groups mark convert
RUN yum groupinstall -y "Development Tools"
RUN yum install -y which wget libffi-devel ruby readline-devel sqlite-devel zlib-devel openssl-devel

# Install Ruby
RUN wget https://cache.ruby-lang.org/pub/ruby/2.6/ruby-2.6.4.tar.gz
RUN tar -xf ruby-2.6.4.tar.gz
WORKDIR ruby-2.6.4
RUN ./configure --prefix=/usr
RUN make
RUN make install
RUN gem install bundler
WORKDIR /
RUN rm -rf ruby-2.6.4.tar.gz ruby-2.6.4

# Install Node
RUN curl -sL https://rpm.nodesource.com/setup_12.x |  bash -
RUN yum install -y nodejs

# Install SQLite3
RUN wget https://www.sqlite.org/2019/sqlite-autoconf-3290000.tar.gz
RUN tar -xf sqlite-autoconf-3290000.tar.gz
WORKDIR sqlite-autoconf-3290000
RUN ./configure --prefix=/usr
RUN make
RUN make install
WORKDIR /
RUN rm -rf sqlite-autoconf-3290000.tar.gz sqlite-autoconf-3290000
WORKDIR /main
