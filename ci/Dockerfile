FROM alpine

RUN apk add --no-cache zip &&\
    apk add --no-cache python && \
    apk add --no-cache --virtual=build-dependencies wget ca-certificates && \
    wget "https://bootstrap.pypa.io/get-pip.py" -O /dev/stdout | python && \
    apk del build-dependencies

ADD requirements.txt .
RUN pip install -r requirements.txt

RUN apk add --no-cache ruby ruby-bundler

RUN gem install bosh_cli --no-ri --no-rdoc

RUN apk add --update bash

RUN apk add openrc
RUN apk add docker
RUN rc-update add docker boot

RUN rm -rf /var/cache/apk/*