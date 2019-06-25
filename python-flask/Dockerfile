FROM python:3.6

RUN apt-get update \
    && apt-get install -y --no-install-recommends gcc g++ build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install freetds for pymssql
WORKDIR /tmp
ENV FREETDS_VER 1.1.6
ENV CFLAGS="-fPIC"
RUN curl ftp://ftp.freetds.org/pub/freetds/stable/freetds-${FREETDS_VER}.tar.gz > freetds-${FREETDS_VER}.tar.gz
RUN tar zxvf freetds-${FREETDS_VER}.tar.gz
WORKDIR /tmp/freetds-${FREETDS_VER}
RUN ./configure --enable-msdblib \
    --prefix=/usr --sysconfdir=/etc/freetds --with-tdsver=7.1 \
    --disable-apps --disable-server --disable-pool --disable-odbc \
    --with-openssl=no --with-gnutls=no
RUN make
RUN make install

# Install Official Microsoft SQL Server Driver and ODBC
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
    && curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list \
    && apt-get update \
    && ACCEPT_EULA=Y DEBIAN_FRONTEND=noninteractive apt-get install -y \
    msodbcsql17 \
    unixodbc-dev \
    && rm -rf /var/lib/apt/lists/* \
    # Adjust Locales to prevemt MS SQL Driver error
    && touch /usr/share/locale/locale.alias \
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && locale-gen

WORKDIR /tmp

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /usr/app

COPY main.py ./

CMD [ "python", "./main.py" ]
