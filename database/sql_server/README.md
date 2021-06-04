# MS-SQL on Linux

```bash
Docker pull : 

sudo docker pull mcr.microsoft.com/mssql/server:2019-latest

Docker start container : 

sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=ThisIsMyDSXMPH@01" -e "MSSQL_PID=Express" \
   -p 1433:1433 --name sql-server -h sql-server \
   -d mcr.microsoft.com/mssql/server:2019-latest

Change Password : 

sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P "<YourStrong@Passw0rd>" \
   -Q 'ALTER LOGIN SA WITH PASSWORD=ThisIsMyDSXMPH@01'

Connecting to Database

sudo docker exec -it sql-server "bash"
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P ThisIsMyDSXMPH@01

Connection string : 

Server=127.0.0.1,1433;Database=tempdb;User Id=SA;Password=ThisIsMyDSXMPH@01
```

