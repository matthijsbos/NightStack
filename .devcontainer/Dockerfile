FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update \
   && apt-get -y install --no-install-recommends \
         git \
         ansible \
         vim \
         python3-dev \
         libffi-dev \
         gcc \
         libssl-dev \
         python3-pip \
         crudini \
         tzdata
RUN pip3 install "kolla-ansible==11.0.0.0rc1"

# Install Docker CE CLI
RUN apt-get update \
    && apt-get install -y apt-transport-https ca-certificates curl gnupg2 lsb-release \
    && curl -fsSL https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]')/gpg | apt-key add - 2>/dev/null \
    && echo "deb [arch=amd64] https://download.docker.com/linux/$(lsb_release -is | tr '[:upper:]' '[:lower:]') $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list \
    && apt-get update \
    && apt-get install -y docker-ce-cli

# Install Docker Compose
RUN LATEST_COMPOSE_VERSION=$(curl -sSL "https://api.github.com/repos/docker/compose/releases/latest" | grep -o -P '(?<="tag_name": ").+(?=")') \
    && curl -sSL "https://github.com/docker/compose/releases/download/${LATEST_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose

# Create kolla config dir according to https://docs.openstack.org/kolla-ansible/victoria/user/quickstart.html#install-kolla-ansible-for-deployment-or-evaluation
RUN  mkdir -p /etc/kolla

# Configure ansible according to https://docs.openstack.org/kolla-ansible/victoria/user/quickstart.html#configure-ansible
RUN crudini --set /etc/ansible/ansible.cfg defaults host_key_checking False
RUN crudini --set /etc/ansible/ansible.cfg defaults pipelining True
RUN crudini --set /etc/ansible/ansible.cfg defaults forks 100


ENV DEBIAN_FRONTEND=dialog