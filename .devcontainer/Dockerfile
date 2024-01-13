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

USER ${USERNAME}

ENV POETRY_VIRTUALENVS_IN_PROJECT=true

RUN \
    curl -sSL https://install.python-poetry.org | python3 - \
    && echo export PATH="${PATH}:${HOME}/.local/bin" >> ~/.bash_profile \
    && source ~/.bash_profile \
    && poetry completions bash >> ~/.bash_completion
