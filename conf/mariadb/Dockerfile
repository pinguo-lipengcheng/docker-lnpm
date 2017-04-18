FROM mariadb:10.1.22
MAINTAINER yokotak0527 <mail@yokotakenji.me>

# 共通ユーザーの作成
ARG AGENT_UID=1000
RUN adduser -D -H -s /bin/sh -u ${AGENT_UID} dev

COPY mariadb.cnf /etc/mysql/conf.d/mariadb.cnf
COPY my.cnf /etc/mysql/my.cnf