FROM python:stretch
RUN curl -SL https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz \
    | tar -xzC /usr/local

RUN curl -SL https://nodejs.org/dist/v12.7.0/node-v12.7.0-linux-x64.tar.xz \
    | tar -xJC /usr/local

ENV PATH="${PATH}:/usr/local/go/bin"
ENV PATH="${PATH}:/usr/local/node-v12.7.0-linux-x64/bin"

RUN apt-get update && apt-get install -y ca-certificates lsb-release gnupg

# gcloud
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
RUN apt-get install -y apt-transport-https ca-certificates 
RUN apt-get update && apt-get install -y google-cloud-sdk

# aws cli
RUN pip3 install awscli --upgrade --user

# azure cli
RUN curl -sL https://packages.microsoft.com/keys/microsoft.asc | \
    gpg --dearmor | \
    tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null

RUN AZ_REPO=$(lsb_release -cs) && echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    tee /etc/apt/sources.list.d/azure-cli.list

RUN apt-get update && apt-get install -y azure-cli


#terraform
RUN wget https://releases.hashicorp.com/terraform/0.12.6/terraform_0.12.6_linux_amd64.zip && unzip terraform_0.12.6_linux_amd64.zip \
    && mv terraform /usr/local/bin && rm terraform_0.12.6_linux_amd64.zip

# docker run --rm -it -p9876:9876 -v `pwd`:/src ps/prefab-scripts
CMD ["bash"]