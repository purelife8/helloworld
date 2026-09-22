FROM redhat/ubi8-minimal:8.10

RUN microdnf install -y \
        gcc-gfortran \
        make \
        git \
        curl \
        tar \
        python3 \
    && microdnf clean all

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \
    | sh -s -- -y

ENV PATH="/root/.cargo/bin:${PATH}"
