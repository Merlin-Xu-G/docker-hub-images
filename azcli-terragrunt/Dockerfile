FROM ubuntu:24.04
WORKDIR /agent
COPY start.sh /agent/start.sh

# Install Azure CLI
RUN apt update && apt install -y curl unzip
RUN curl -sL https://aka.ms/InstallAzureCLIDeb | bash

# Install Terraform
RUN curl -fsSL https://apt.releases.hashicorp.com/gpg | apt-key add - && \
    apt-add-repository "deb [arch=i386] https://apt.releases.hashicorp.com $(lsb_release -cs) main" && \
    apt update && \
    apt install -y terraform

# Install Terragrunt
RUN TERRAGRUNT_VERSION=$(curl -s https://api.github.com/repos/gruntwork-io/terragrunt/releases/latest | grep tag_name | cut -d '"' -f 4) && \
    curl -Lo /usr/local/bin/terragrunt https://github.com/gruntwork-io/terragrunt/releases/download/${TERRAGRUNT_VERSION}/terragrunt_linux_386 && \
    chmod +x /usr/local/bin/terragrunt


CMD ["bash"]