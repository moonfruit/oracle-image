FROM dkmoonfruit/oracle:18.4.0-xe

ENV ORACLE_PWD=oracle \
    ORACLE_CHARACTERSET=AL32UTF8

COPY initOracle.patch $INSTALL_DIR/
RUN yum -y install patch && \
    cp $ORACLE_BASE/$RUN_FILE $INSTALL_DIR/initOracle.sh && \
    patch $INSTALL_DIR/initOracle.sh < $INSTALL_DIR/initOracle.patch && \
    yum -y erase patch && \
    rm -rf /var/cache/yum && \
    rm -rf /var/tmp/yum-*

RUN $INSTALL_DIR/initOracle.sh && \
    rm -rf $INSTALL_DIR

CMD exec $ORACLE_BASE/$RUN_FILE
