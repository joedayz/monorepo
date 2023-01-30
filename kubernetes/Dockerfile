FROM jenkins/jenkins:2.361.4-lts-jdk11
RUN jenkins-plugin-cli --plugins "blueocean:1.27.1 git:5.0.0"

# install Maven
USER root
RUN apt-get update && apt-get install -y maven curl apt-transport-https ca-certificates gnupg2 unzip xvfb libxi6 libgconf-2-4
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y build-essential nodejs
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN echo "deb [arch=amd64] https://download.docker.com/linux/debian stretch stable" >> /etc/apt/sources.list
RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | tee -a /etc/apt/sources.list.d/kubernetes.list
RUN apt-get update
RUN apt-get install -y docker-ce kubectl
EXPOSE 80