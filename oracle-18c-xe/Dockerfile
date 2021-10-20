FROM gvenzl/oracle-xe:18.4.0-slim

ENV ORACLE_PASSWORD=test \
    APP_USER=test \
    APP_USER_PASSWORD=test

COPY container-initialize.patch cleanup.sh /install/

USER root
RUN cp container-entrypoint.sh /install/container-initialize.sh && \
    microdnf -y install patch && \
    patch /install/container-initialize.sh < /install/container-initialize.patch && \
    microdnf -y remove patch && \
    microdnf clean all && \
    chown oracle:dba /install/container-initialize.sh && \
    chmod 4755 /install/cleanup.sh

USER oracle
RUN /install/container-initialize.sh && \
    /install/cleanup.sh
