FROM mysql:8.0

# Set default environment variables
ENV MYSQL_ROOT_PASSWORD=changeme
ENV MYSQL_DATABASE=ghost
ENV MYSQL_USER=ghost
ENV MYSQL_PASSWORD=changeme

# MySQL configuration for Ghost compatibility
COPY --chown=mysql:mysql mysql/my.cnf /etc/mysql/conf.d/

EXPOSE 3306