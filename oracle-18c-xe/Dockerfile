FROM dkmoonfruit/oracle:18.4.0-xe

ENV ORACLE_PWD=oracle \
    ORACLE_CHARACTERSET=AL32UTF8

RUN $ORACLE_BASE/$RUN_FILE
RUN systemctl stop oracle-xe-18c

CMD exec $ORACLE_BASE/$RUN_FILE
