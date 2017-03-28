FROM python:3.5
WORKDIR /opt/test
COPY requirements.txt requirements.txt
RUN pip install uwsgi -r requirements.txt
COPY . .
RUN groupadd -r -g 999 application && \
    useradd -r -g application application && \
    chown -R application:application .
RUN mkdir /run/test && \
    chown application:application /run/test
VOLUME /opt/test \
       /run/test
CMD uwsgi config/application/uwsgi.ini
