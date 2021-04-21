ARG BASE_IMAGE=jupyterhub/k8s-hub:0.11.1
FROM "${BASE_IMAGE}"

USER root
RUN apt-get update \
 && apt-get install -y \
    unzip \
    wget \
 && rm -rf /var/lib/apt/lists/*

USER "${NB_UID}"

ARG GITHUB_TOKEN

ENV PATH="/home/${NB_USER}/.local/bin:${PATH}"
RUN --mount=type=secret,id=github_token \
  cat /run/secrets/github_token

# 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



# illumidesk package
ARG ILLUMIDESK_VERSION=3.0.0
# apple connect proxy authenticator package
ARG ACP_AUTH_VERSION=0.1.0

# ensure pip is up to date
RUN python3 -m pip install --upgrade pip

COPY requirements.txt /tmp/
RUN pip install -r /tmp/requirements.txt

WORKDIR /tmp
RUN wget "https://github.com/IllumiDesk/illumidesk/archive/v${ILLUMIDESK_VERSION}.zip" \
 && unzip "/tmp/v${ILLUMIDESK_VERSION}.zip"
WORKDIR "/tmp/illumidesk-${ILLUMIDESK_VERSION}/src/illumidesk/"
RUN python3 -m pip install .

WORKDIR /tmp
RUN python3 -m pip install "git+https://${GITHUB_TOKEN}@github.com/illumidesk/appleconnectauthenticator.git@${ACP_AUTH_VERSION}"

WORKDIR /srv/jupyterhub/

COPY illumidesk-80.png /srv/jupyterhub/illumidesk-80.png
COPY jupyterhub_config.py /srv/jupyterhub/
COPY wait-for-postgres.sh /srv/jupyterhub/

CMD ["./wait-for-postgres.sh", "jupyterhub", "--config", "/srv/jupyterhub/jupyterhub_config.py"]
