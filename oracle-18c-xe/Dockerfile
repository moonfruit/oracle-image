FROM gvenzl/oracle-xe:18.4.0-slim

ENV ORACLE_PASSWORD=test \
    APP_USER=test \
    APP_USER_PASSWORD=test

COPY container-initialize.patch ${ORACLE_BASE}
RUN cp container-entrypoint.sh container-initialize.sh && \
    microdnf -y install patch && \
    patch container-initialize.sh < container-initialize.patch && \
    microdnf -y remove patch && \
    microdnf clean all && \
    container-initialize.sh && \
    rm -fr container-initialize.*
