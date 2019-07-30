# php-mysql-phpmyadmin-demo-repicate-docker
Thực hành Mysql Replicate Môi trường docker

Repo gốc https://github.com/webdevops/php-docker-boilerplate
Yêu cầu docker * https://docs.docker.com/compose/install/ *

## Bước 1
git clone 
## Bước 2
docker-composer up
## Bước 3: test phpmyadmin
 - master: localhost:8001  
    root/dev
 - slave: localhost:8002  
    root/dev

## Bước 4: Setup Master
 - master: localhost:8001  
    root/dev
 - Thực hiện Sql: show master status;
 - Ghi nhớ posions
 - Tạo user slave sql: GRANT REPLICATION SLAVE ON *.* TO 'slave_user'@'%' IDENTIFIED BY 'password';       FLUSH PRIVILEGES; 
 - Export db
## Bước 5 Setup Slave
 - slave: localhost:8002  
    root/dev
 - Import db
 - Xem ip hiện tại bật terminal: docker inspect php-docker-boilerplate-master_phpmyadmin_master_1
 - Thực hiện Sql: CHANGE MASTER TO MASTER_HOST='12.34.56.789',MASTER_USER='slave_user', MASTER_PASSWORD='password', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=  107;
 - Thực hiện Sql: START SLAVE; 
 - Kiểm tra: SHOW SLAVE STATUS;
 

