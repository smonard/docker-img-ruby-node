FROM fedora

RUN dnf upgrade -y
RUN dnf install -y java-latest-openjdk
RUN dnf install -y nodejs
WORKDIR /prj/
RUN touch .keep

CMD [ "cat /etc/os-release && uname -a" ]
ENTRYPOINT [ "/bin/sh", "-c" ]