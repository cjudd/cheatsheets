# PostgreSQL Cheat Sheet
By Christopher M. Judd (javajudd@gmail.com)

## Resources
* https://www.postgresqltutorial.com/postgresql-cheat-sheet/

## CLI
```
psql
psql -U [username]
sudo -u postgres psql
```

### Quit
```
\q
```

### Connect to database
```
\c database_name;
```

### List All (Show) Databases
```
\l
```

### List Schemas
```
\dn
```

### List stored procedures & functions
```
\df
```

### List views
```
\dv
```

### List tables
```
\dt
\dt+
```

### Table Details
```
\d+ table_name
```

### List users
```
\du
```