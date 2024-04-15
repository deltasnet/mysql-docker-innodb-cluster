FROM oraclelinux:8-slim

ARG KEY=https://repo.mysql.com/RPM-GPG-KEY-mysql
ARG REPO=https://repo.mysql.com
ARG MYSQL_SHELL_PACKAGE=mysql-shell-8.0.36-1.el8.x86_64.rpm
ARG MYSQL_SHELL_PACKAGE_URL=$REPO/yum/mysql-tools-community/el/8/x86_64/$MYSQL_SHELL_PACKAGE

RUN microdnf install -y wget       \
  && microdnf install python3.9    \
  && rpmkeys --import $KEY         \
  && wget $MYSQL_SHELL_PACKAGE_URL \
  && rpm -i $MYSQL_SHELL_PACKAGE   \
  && microdnf clean all
COPY run.sh /run.sh
ENTRYPOINT ["/run.sh"]
CMD ["mysqlsh"]
