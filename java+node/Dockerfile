FROM fedora

RUN dnf upgrade -y
RUN dnf install -y java-latest-openjdk
RUN dnf install -y nodejs
WORKDIR /server/
ENV JAVA_HOME=/usr/lib/jvm/java-15-openjdk-15.0.1.9-9.rolling.fc33.x86_64/
RUN touch .keep

CMD [ "cat /etc/os-release && uname -a && java --version && echo Node-env: && node --version && npm --version" ]
ENTRYPOINT [ "/bin/sh", "-c" ]