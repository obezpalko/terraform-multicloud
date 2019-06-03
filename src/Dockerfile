
FROM chef/chefdk

ENV TERRAFORM_VERSION 0.12.0
ENV container docker
ENV LC_ALL C
ENV DEBIAN_FRONTEND noninteractive
ENV HOME /terraform

RUN useradd terraform --base-dir / --create-home --user-group

RUN apt-get update && \
    apt-get install -y groff jq coreutils zip apt-utils unzip git bash openssh-client python3 python3-pip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
RUN pip3 install awscli

RUN curl -o /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip
RUN unzip /tmp/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -d /usr/bin

WORKDIR /terraform
USER terraform
