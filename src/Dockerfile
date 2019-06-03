
FROM chef/chefdk

ENV TERRAFORM_VERSION 0.12.0
ENV container docker
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive
ENV SSH_AUTH_MOUNT /tmp/ssh-auth
ENV SSH_AUTH_SOCK ${SSH_AUTH_MOUNT}/S.gpg-agent.ssh
ENV HOME /root

RUN curl -o /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip


RUN apt-get update && \
    apt-get install -y groff jq coreutils zip apt-utils unzip git bash openssh-client python3 python3-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN pip3 install awscli

RUN unzip /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /usr/bin

# docker build -t $(basename $(pwd)):latest .
# docker run --rm --name terraform-multicloud -it -v $(dirname $SSH_AUTH_SOCK):/tmp/ssh-auth -v ~/.aws:/root/.aws:ro -v ~/.chef:/root/.chef:ro -v /etc/resolv.conf:/etc/resolv.conf:ro -e USER terraform-multicloud 
