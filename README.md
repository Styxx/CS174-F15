CS 174A Final Project

Sahil Bissessur and Vincent Chang


Server Setup:
1. SSH into AWS instance (joog1)
2. Edit config file: `sudo vim /etc/mysql/my.cnf`
3. Change bind-address to server private IP
4. Restart MySQL service: `sudo service mysql restart`
  a. If it's taking too long to restart, make sure you have the correct IP
5. Compile UDF: `make udf`
6. Login to MySQL terminal: `mysql -u root -p`
7. Initialize database: `source initialize.sql`
8. Use correct database: `mysql> use project;`
9. Create function: `CREATE AGGREGATE FUNCTION SUM_HE RETURNS STRING SONAME 'sum_he.so';
10. Give client access: `GRANT ALL ON project.\* TO root@<client public IP> IDENTIFIED BY 'cs174$';



Client Setup:
1. Install GMP and paillier library if not done beforehand.
2. Change connection IP to server public IP in `queries.c`.
3. Compile and run client: `make` `./client`


To generate paillier keys:
Compile and run `generateKeys.c`.
Keys will be located in `paillierKeys.txt`.
Compile code is in `gccCommands.txt`

Files submitted: queries.c, SUM_HE.c, libpaillier-0.8/, Makefile. initialize.sql, paillierKeys.txt, joogKey.pem, README.md, gccCommands.txt, generateKeys.c
