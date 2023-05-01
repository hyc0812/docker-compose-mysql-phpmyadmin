# docker-compose-mysql-phpmyadmin

```
version: "3"

services:
  # Database
  db:
    image: mysql:5.7
    volumes:
      - /Users/yongchanghe/Desktop/db_data:/var/lib/mysql
    restart: always
    ports:
      - "3306:3306"
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: cake_cms
      MYSQL_PASSWORD: password
    networks:
      - mysql-phpmyadmin

  # phpmyadmin
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin
    restart: always
    ports:
      - "8090:80"
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: password
    networks:
      - mysql-phpmyadmin

networks:
  mysql-phpmyadmin:

volumes:
  db_data:

```
  
  
