# PITR

> Document：[continuous-archiving](https://www.postgresql.org/docs/9.6/static/continuous-archiving.html)

## Backgroud

At all times, PostgreSQL maintains a write ahead log \(WAL\) in the pg\_xlog/ subdirectory of the cluster's data directory. The log records every change made to the database's data files. if the system crashes, the database can be restored to consistency by "replaying" the log entries made since the last checkpoint.

## Priority

* Dont need a perfectly consistent file system backup as the starting point
* Dont need take a full backup frequently
* Restore the databse to its state at any time
* file-system-level backups

## Procedure

### Setting Up WAL Archiving

Save the following setting in **postgresql.conf**, and  always to test your proposed archive\_command. Once pg\_xlog/ fills up, PostgreSQL will do a PANIC shutdown.

```text
wal_level = archive
archive_mode = on
archive_command = 'test !-f /var/lib/postgresql/data/%f && cp %p /var/lib/postgresql/data/archive/%f'
```

* Other Parameters:
  * archive\_timeout : to force the server to switch a new WAL segment file at least that often
  * pg\_switch\_xlog : ensure that a just-finished transaction is archived.

### Making a Base Backup

```text
select pg_start_backup('label',true);
tar -zxcf data.tar.gz ./data
tar -zxcf pg_xlog.tar.gz ./data/pg_xlog
tar -zxcf pg_tablspc.tar.gz ./data/pg_tablspc
select pg_stop_backup();
```

* Files should be Omitted from data dir:
  * pg\_xlog/
  * postmaster.pid & postmaster.opts
  * pg\_replslot
* Backup lable file
  * string in pg\_start\_backup and time

### Recovering Using a Continuous Archive Backup

Firstly verify symbolic link in pg\_tablspc while using tablespace, then create **recovery.conf** in data directory

```text
recovery_command = 'cp /var/lib/postgresql/data/%f %p'
recovery_target_time = '2017-10-18 16:10:00+08'
```

Then start the server. Once the recovery process is completed, recovery.conf will be renamed to **recovery.done**

## Caveats

* Operations on the hash indexes are not presently WAL-logged. REINDEX is  needed after recovery.
* Not to modify any template databases while taking a base backup.
* CRATE TABLESPACE are WAL-logged with absolute path.

