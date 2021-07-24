FROM fedora
RUN useradd wasm
RUN dnf update -y
RUN dnf install -y make automake gcc gcc-c++ cmake python3 python3-pip git xz bzip2 \
    && ln -s /usr/bin/python3 /usr/bin/python
USER wasm
WORKDIR /home/wasm
RUN git clone https://github.com/emscripten-core/emsdk.git \
    && cd emsdk \
    && ./emsdk install latest \
    && ./emsdk activate latest \
    && echo 'source ${HOME}/emsdk/emsdk_env.sh' >> /home/wasm/.bashrc
ENTRYPOINT [ "/bin/bash" ]

