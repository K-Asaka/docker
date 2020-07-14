FROM jenkins/jenkins

USER root
RUN apt-get update \
    && apt-get install -y \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
    && apt-key fingerprint 0EBFCD88 \
    && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" \
    && apt-get update \
    && apt-get install -y \
        docker-ce \
        docker-ce-cli \
        containerd.io \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN usermod -aG docker jenkins

RUN cd /tmp/ \
    && wget https://updates.jenkins-ci.org/latest/jenkins.war \
    && mv ./jenkins.war /usr/share/jenkins/

USER jenkins
