FROM python:3.7

WORKDIR /tmp

RUN curl http://ftp.us.debian.org/debian/pool/main/a/apt/apt-transport-https_1.4.9_amd64.deb > apt-transport-https.deb \
    && dpkg -i apt-transport-https.deb

# Install Official Microsoft SQL Server Driver and ODBC
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
    && curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list \
    && apt-get update \
    && ACCEPT_EULA=Y apt-get install \
    apt-transport-https \
    msodbcsql17 \
    vim \
    && rm -rf /var/lib/apt/lists/* \
    # Adjust Locales to prevemt MS SQL Driver error
    && touch /usr/share/locale/locale.alias \
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && locale-gen

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /usr/app

COPY main.py ./

CMD [ "python", "./main.py" ]
