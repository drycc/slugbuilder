ARG STACK

FROM docker.io/minio/mc:latest as mc


FROM docker.io/drycc/stack-images:${STACK}-build

ENV STACK heroku-${STACK}
ENV DEBIAN_FRONTEND noninteractive
ENV PYTHONPATH $PYTHONPATH:/usr/local/lib/python3/site-packages

ADD . /
COPY --from=mc /usr/bin/mc /bin/mc

RUN /installer/install

USER slug
WORKDIR /tmp
ENV HOME /app

ENTRYPOINT ["/builder/build.sh"]
