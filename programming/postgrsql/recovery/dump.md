# dump

The idea behind this dump method is to generate a file with SQL commands that, when fed back to the server, will recreate the database in the same state as it was at the time of the dump.

## Merits and Drawbacks

* Merits
  * The file is smaller
* Drawbacks
  * backup to the state of pg\_dump
  * Only have the logical contents of database, lost all the detail history
  * have sufficient privileges to back up potions of the database

## backup

```sql
pg_dump dbname -n schema -t table | gzip > outfile
```

## restore

```sql
psql dbname < infile
```

