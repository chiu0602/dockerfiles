FROM jupyter/datascience-notebook

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends mysql-devel \
    && rm -rf /var/lib/apt/lists/*

[mtr@localhost jupyter-mysql]$ cd ..
[mtr@localhost sc-monitor2]$ mv jupyter-mysql datascience-notebook
[mtr@localhost sc-monitor2]$ cd datascience-notebook
[mtr@localhost datascience-notebook]$ ;s
-bash: syntax error near unexpected token `;'
[mtr@localhost datascience-notebook]$ ls
build.sh  Dockerfile
[mtr@localhost datascience-notebook]$ cat Dockerfile
FROM jupyter/datascience-notebook

USER root

RUN apt-get update \
    && apt-get install -y --no-install-recommends mysql-devel \
    && rm -rf /var/lib/apt/lists/*

pip install --no-cache-dir mysqlclient
