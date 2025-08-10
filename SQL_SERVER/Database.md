 Windows Users:

Find the SQL Server service account name run in SSMS as sysadmin:
```sql
SELECT servicename, service_account
FROM sys.dm_server_services;
```

Verify SQL Server can see the folder
```sql
EXEC xp_fileexist 'C:\BDPN_SQL_SERVER';
```


run in SSMS: 
```sql
CREATE DATABASE BDPN
ON PRIMARY 
(
    NAME = BDPN,
    FILENAME = 'C:\BDPN_SQL_SERVER\BDPN_Data.mdf',
    SIZE = 10MB,
    MAXSIZE = 100MB,
    FILEGROWTH = 5MB
)
LOG ON
(
    NAME = BDPN_Log,
    FILENAME = 'C:\BDPN_SQL_SERVER\BDPN_Log.ldf',
    SIZE = 5MB,
    MAXSIZE = 25MB,
    FILEGROWTH = 5MB
);
```

Mac Users:
 run in SSMS: 
```sql
CREATE DATABASE BDPN;
```
