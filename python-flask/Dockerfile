FROM python:3

RUN apt-get update \
    && apt-get install -y --no-install-recommends freetds-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

RUN curl -L --insecure http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz -o ta-lib-0.4.0-src.tar.gz && \
    tar -xvzf ta-lib-0.4.0-src.tar.gz && \
    cd ta-lib/ && \
    ./configure --prefix=/usr && \
    make && make install

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /usr/src/app

COPY main.py ./

CMD [ "python", "./main.py" ]
