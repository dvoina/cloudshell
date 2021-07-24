FROM fedora
RUN useradd rust
RUN dnf update -y
RUN dnf install -y make automake gcc gcc-c++ cmake python3 python3-pip git xz bzip2 \
    && ln -s /usr/bin/python3 /usr/bin/python
USER rust
WORKDIR /home/rust
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
ENTRYPOINT [ "/bin/bash" ]


