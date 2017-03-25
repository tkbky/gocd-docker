FROM ubuntu:16.04
MAINTAINER KY <infcurious@gmail.com>

RUN apt-get update
RUN apt-get install -qqy curl apt-transport-https default-jre openssh-client git-core

RUN echo "deb https://download.gocd.io /" | tee /etc/apt/sources.list.d/gocd.list
RUN curl https://download.gocd.io/GOCD-GPG-KEY.asc | apt-key add -

RUN apt-get update
RUN apt-get install -qqy go-server
RUN update-java-alternatives --set java-1.8.0-openjdk-amd64

EXPOSE 8153
EXPOSE 8154

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

CMD ["/etc/init.d/go-server", "start"]
CMD /etc/init.d/go-server start && tail -f /var/log/go-server/go-server.log
