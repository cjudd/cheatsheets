# Oracle Cheat Sheet

## Docker
### Start
```
docker run -d -it --name oracle-db -p 1521:1521 -p 5500:5500 -v /tmp/oracle-db/:/ORCL store/oracle/database-enterprise:12.2.0.1-slim
```
### Launch PLSQL
```
docker exec -it oracleDb bash -c "source /home/oracle/.bashrc; sqlplus /nolog"
```

## PLSQL
### Login
```
connect SYS AS SYSDBA
```
password is Oradoc_db1
