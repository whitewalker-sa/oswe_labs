# Use the official MySQL 8 image
FROM mysql:8.0

# Copy custom MySQL configurations if needed
# Uncomment and modify if you have a custom configuration
COPY ./my.cnf /etc/mysql/my.cnf

# Expose the MySQL port
EXPOSE 3306

# Default command (inherited from the MySQL image)
CMD ["mysqld"]
