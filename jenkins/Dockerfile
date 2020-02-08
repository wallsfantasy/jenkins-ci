FROM jenkins/jenkins:lts

# suggested method to run apt when extended from jenkins:lts
# https://github.com/jenkinsci/docker/blob/master/README.md#installing-more-tools
USER root
ARG DEBIAN_FRONTEND=noninteractive

# install required packages for docker-ce
RUN apt-get update -qq && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common

# install docker-ce
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" && \
apt-get update -qq && apt-get install docker-ce -y

# post-install docker-ce
RUN usermod -aG docker jenkins
