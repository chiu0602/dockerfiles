FROM python:3

RUN apt-get update \
    && apt-get install -y --no-install-recommends freetds-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /usr/src/app

COPY main.py ./

CMD [ "python", "./main.py" ]
