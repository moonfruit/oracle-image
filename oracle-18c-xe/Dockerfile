FROM gvenzl/oracle-xe:18.4.0-slim

ENV ORACLE_PASSWORD=test \
    APP_USER=test \
    APP_USER_PASSWORD=test

COPY container-initialize.patch /install/

RUN cp ${ORACLE_BASE}/container-entrypoint.sh /install/container-initialize.sh && \
    microdnf -y install patch && \
    patch /install/container-initialize.sh < /install/container-initialize.patch && \
    microdnf -y remove patch && \
    microdnf clean all && \
    /install/container-initialize.sh && \
    rm -f /install
