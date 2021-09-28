FROM mysql

ENV MYSQL_ROOT_PASSWORD=root \
    MYSQL_USER=user \
    MYSQL_PASSWORD=pass \
    MYSQL_DATABASE=my_db

COPY mysql-init.sql /tmp/mysql-init.sql

EXPOSE 3306

CMD ["--init-file=/tmp/mysql-init.sql", "--default-authentication-plugin=mysql_native_password"]
