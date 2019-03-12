FROM browserless/chrome
USER root
WORKDIR /root
ENV LANG=en_US.UTF-8
EXPOSE 8443

RUN apt-get update && apt-get install -y openssl net-tools locales && locale-gen en_US.UTF-8

RUN wget https://github.com/codercom/code-server/releases/download/1.31.1-100/code-server-1.31.1-100-linux-x64.tar.gz && tar xfz code-server-1.31.1-100-linux-x64.tar.gz && mkdir ~/.code-server/extensions/ -p && mv /root/code-server-1.31.1-100-linux-x64/code-server /usr/local/bin/
RUN wget https://marketplace.visualstudio.com/_apis/public/gallery/publishers/auchenberg/vsextensions/vscode-browser-preview/0.4.0/vspackage --output-document=preview.zip.gz && gunzip preview.zip.gz && unzip preview.zip && mv extension ~/.code-server/extensions/vscode-browser-preview/
RUN cd /usr/local/bin/ && wget https://releases.hashicorp.com/terraform/0.11.13/terraform_0.11.13_linux_amd64.zip && unzip -x terraform_0.11.13_linux_amd64.zip && rm terraform_0.11.13_linux_amd64.zip && chmod +x terraform

ENTRYPOINT [ "code-server" ]
CMD ["--allow-http"]


