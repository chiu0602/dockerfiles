FROM jupyter/datascience-notebook

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends libmysqlclient-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir mysqlclient
