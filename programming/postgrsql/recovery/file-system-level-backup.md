# file system level backup

## Restrictions

* The database server must be shut down
* Can't back up or restore only certain individual tables or databases

## Command

```text
tar -cf backup.tar /usr/local/pgsql/data
```

