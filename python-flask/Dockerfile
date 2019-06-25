FROM python:3.6

RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc g++ build-essential \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp
ENV FREETDS_VER 1.1.6
ENV CFLAGS="-fPIC"
RUN curl ftp://ftp.freetds.org/pub/freetds/stable/freetds-${FREETDS_VER}.tar.gz
RUN tar zxvf freetds-${FREETDS_VER}.tar.gz
WORKDIR /tmp/freetds-${FREETDS_VER}
RUN ./configure --enable-msdblib \
    --prefix=/usr --sysconfdir=/etc/freetds --with-tdsver=7.1 \
    --disable-apps --disable-server --disable-pool --disable-odbc \
    --with-openssl=no --with-gnutls=no
RUN make
RUN make install

WORKDIR /tmp

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /usr/app

COPY main.py ./

CMD [ "python", "./main.py" ]
