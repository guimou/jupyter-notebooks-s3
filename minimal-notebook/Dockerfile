FROM centos/python-36-centos7:latest
ARG JUPYTERHUB_VERSION=1.0.0
USER root

COPY . /tmp/src

RUN rm -rf /tmp/src/.git* && \
    chown -R 1001 /tmp/src && \
    chgrp -R 0 /tmp/src && \
    chmod -R g+w /tmp/src && \
    rm -rf /tmp/scripts && \
    mv /tmp/src/.s2i/bin /tmp/scripts

USER 1001

RUN /tmp/scripts/assemble

CMD [ "/opt/app-root/builder/run" ]
