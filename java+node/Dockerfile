FROM fedora:39

RUN dnf update -y
RUN dnf install -y wget unzip xz
RUN dnf groupinstall -y "Development Tools"

# JAVA 15
RUN wget https://download.java.net/openjdk/jdk15/ri/openjdk-15+36_linux-x64_bin.tar.gz \
  && tar -xvf openjdk-15+36_linux-x64_bin.tar.gz \
  && rm openjdk-15+36_linux-x64_bin.tar.gz
ENV JAVA_HOME=/jdk-15/
ENV PATH="$JAVA_HOME/bin:$PATH"

# NODE 18
RUN wget https://nodejs.org/dist/v18.18.2/node-v18.18.2-linux-x64.tar.xz \
  && tar -xvf node-v18.18.2-linux-x64.tar.xz \
  && rm node-v18.18.2-linux-x64.tar.xz
ENV PATH="/node-v18.18.2-linux-x64:$PATH"
ENV PATH="/node-v18.18.2-linux-x64/bin/:$PATH"

RUN wget https://services.gradle.org/distributions/gradle-6.8.1-bin.zip \
  && unzip -d /opt/gradle gradle-6.8.1-bin.zip \
  && rm gradle-6.8.1-bin.zip
ENV PATH="${PATH}:/opt/gradle/gradle-6.8.1/bin"

RUN ln -sf /usr/share/zoneinfo/America/Guayaquil /etc/localtime

WORKDIR /server/
RUN touch .keep

CMD [ "cat /etc/os-release && uname -a && java --version && echo Node-env: && node --version && npm --version" ]
ENTRYPOINT [ "/bin/sh", "-c" ]
