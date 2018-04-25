FROM jupyter/datascience-notebook

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends mysql-devel \
    && rm -rf /var/lib/apt/lists/*

pip install --no-cache-dir mysqlclient
