FROM dkmoonfruit/oracle:18.4.0-xe

ENV ORACLE_PWD=oracle \
    ORACLE_CHARACTERSET=AL32UTF8

COPY initOracle.sh $INSTALL_DIR/
RUN $INSTALL_DIR/initOracle.sh && \
    rm -rf $INSTALL_DIR

CMD exec $ORACLE_BASE/$RUN_FILE
