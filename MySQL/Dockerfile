FROM mysql

ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_USER=user
ENV MYSQL_PASSWORD=pass 
ENV MYSQL_DATABASE=my_db

COPY mysql-init.sql /tmp/mysql-init.sql

EXPOSE 3306

CMD ["--init-file=/tmp/mysql-init.sql", "--default-authentication-plugin=mysql_native_password"]
