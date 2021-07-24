FROM fedora

RUN useradd --shell /usr/bin/zsh ansible
WORKDIR /home/ansible
RUN dnf update -y
RUN dnf install -y git zsh python3-wheel python3-pip unzip openssl

#install ansible
RUN pip install ansible

#install aws-cli
RUN curl -LO https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip \
    && unzip awscli-exe-linux-x86_64.zip \
    && ./aws/install \
    && rm -rf aws awscli-exe-linux-x86_64.zip

#install kubectl
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && chmod a+x kubectl \
    && mv kubectl /usr/local/bin

#install helm
RUN curl -LO https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 \
    && sh ./get-helm-3 \
    && rm -f get-helm-3

#last tweaks
USER ansible

#install ZSH goodies
RUN  sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"  -t blinks
RUN echo 'ZSH_THEME="blinks"' >> /home/ansible/.zshrc \
    && echo 'plugins=(ansible git helm kubernetes)' >> /home/ansible/.zshrc
ENTRYPOINT [ "/usr/bin/zsh" ]



