FROM ubuntu:latest
RUN mkdir /tools
WORKDIR /tools
RUN apt-get update && apt-get install -y \
    curl \
    python \
    sshpass \
    wget \
    unzip \
    git \
    jq \
    nano \
    apt-utils \
    && rm -rf /var/lib/apt/lists/* && \
    wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    apt update -y && \
    apt install powershell -y && \
    rm -rf /tools/* && \
    find /tools/ -name "*.sh" -execdir chmod u+x {} +
SHELL [ "pwsh", "-command" ]
RUN Set-PSRepository -Name PSGallery -InstallationPolicy Trusted
RUN Install-Module VMware.PowerCLI,PowerNSX,PowervRA
RUN Set-PowerCLIConfiguration -InvalidCertificateAction:ignore -Confirm:$false
CMD ["/bin/pwsh"]
