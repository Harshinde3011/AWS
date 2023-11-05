
### Adding some dummy data to the Database inside EC2 Instance:
```bash
In ec2 instance 
mysql -u root --password="${DBRootPassword}"
USE ec2db;
CREATE TABLE table1 (id INT, name VARCHAR(45));
INSERT INTO table1 VALUES(1, 'Virat'), (2, 'Sachin'), (3, 'Dhoni'), (4, 'ABD');
SELECT * FROM table1;
```
### Migration of Database in EC2 Instance to RDS Database:

```bash
First create RDS instance and install Mariadb in that

run below command in ec2 to create dump db of your current db
mysqldump -u root -p ec2db > ec2db.sql

exit from db and run this command 
mysql -h <replace-rds-end-point-here> -P 3306 -u rdsuser -p rdsname < ec2db.sql
mysql -h <replace-rds-end-point-here> -P 3306 -u rdsuser -p
USE rdsname
SELECT * FROM table1;
```



