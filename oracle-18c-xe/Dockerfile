FROM gvenzl/oracle-xe:18.4.0-slim

ENV ORACLE_PASSWORD=test \
    APP_USER=test \
    APP_USER_PASSWORD=test

COPY container-initialize.patch .

USER root
RUN cp container-entrypoint.sh container-initialize.sh && \
    microdnf -y install patch && \
    patch container-initialize.sh < container-initialize.patch && \
    microdnf -y remove patch && \
    microdnf clean all && \
    rm container-initialize.patch && \
    chown oracle:dba container-initialize.sh

USER oracle
RUN container-initialize.sh && \
    rm container-initialize.sh
