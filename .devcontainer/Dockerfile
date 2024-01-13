FROM python:3.12.1

WORKDIR /work

ARG USERNAME

SHELL ["/bin/bash", "-c"]

RUN apt update && apt install -y \
        iputils-ping \
        iproute2 \
        jq \
        dnsutils \
        sysstat \
        lsof \
        nkf \
        socat \
        nodejs npm \
    && apt clean \
    && rm -rf /var/lib/apt/lists/* \
    && groupadd ${USERNAME} \
    && useradd -d /home/${USERNAME} -s /bin/bash -g ${USERNAME} -m ${USERNAME} \
    && mkdir -m 777 /workspaces \
    && npm install -g git-cz
