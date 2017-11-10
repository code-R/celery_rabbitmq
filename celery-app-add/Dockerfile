FROM ubuntu:16.04

RUN apt-get update && apt-get -y upgrade && apt-get install -y build-essential && apt-get install -y software-properties-common && apt-get install -y byobu curl git htop man unzip vim wget python python-dev python-pip python-virtualenv && rm -rf /var/lib/apt/lists/*

USER root

ENV CELERY_VERSION 4.1.0

RUN pip install celery=="$CELERY_VERSION"

ADD celery_conf.py /data/celery_conf.py
ADD run_tasks.py /data/run_tasks.py
ADD run.sh /usr/local/bin/run.sh

ENV C_FORCE_ROOT 1

WORKDIR /data

CMD ["/bin/bash", "/usr/local/bin/run.sh"]