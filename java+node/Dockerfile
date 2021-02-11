FROM fedora

RUN dnf upgrade -y
RUN dnf install -y wget unzip
RUN dnf install -y ruby

RUN dnf install -y java-latest-openjdk java-latest-openjdk-devel
ENV JAVA_HOME=/usr/lib/jvm/java-15-openjdk-15.0.2.0.7-0.rolling.fc33.x86_64/

RUN dnf install -y nodejs

RUN wget https://services.gradle.org/distributions/gradle-6.8.1-bin.zip
RUN unzip -d /opt/gradle gradle-6.8.1-bin.zip
ENV PATH="${PATH}:/opt/gradle/gradle-6.8.1/bin"
RUN rm gradle-6.8.1-bin.zip

RUN ln -sf /usr/share/zoneinfo/America/Guayaquil /etc/localtime

WORKDIR /server/
RUN touch .keep

CMD [ "cat /etc/os-release && uname -a && java --version && echo Node-env: && node --version && npm --version" ]
ENTRYPOINT [ "/bin/sh", "-c" ]
