FROM python:{{cookiecutter.python_version}}


RUN DEBIAN_FRONTEND=noninteractive apt-get update \
    && apt-get install -y \
        locales

ENV DOCKER true
ENV PYTHONPATH $PYTHONPATH:/app
ENV LC_ALL C.UTF-8
ENV LANG C.UTF-8

ADD ./dev /app/dev

# INSTALL python dependencies & test
RUN cd /app && ./dev/install.sh

# TODO: Exclude tests for deployment
ADD . /app

EXPOSE 8090
EXPOSE 8888

WORKDIR /app
ENTRYPOINT ["./manage.py start"]
