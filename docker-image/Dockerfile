FROM microsoft/azure-cli

# Install Helm
RUN curl -L https://git.io/get_helm.sh | bash

# Install Kubectl
RUN curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
RUN chmod +x ./kubectl
RUN mv ./kubectl /usr/local/bin

# Add entrypoint
COPY boot-strap.sh /
RUN chmod 777 boot-strap.sh

CMD ["/boot-strap.sh"]
