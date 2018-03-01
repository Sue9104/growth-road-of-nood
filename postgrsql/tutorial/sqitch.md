# Sqitch使用
## 特点
- Migration
 - Incomplete mini-language
 - No logical replication integration
 - Numbered scripts hard to track
 - No VCS awareness

- 优点
 - No opinions
 - Native scripting (psql, sqlite3, SQL*Plus)
 - Cross-project dependency resolution
 - Distribution bundling
 - Integrated verification testing
 - No numbering
 - Reliable sequential deployment ordering
## 使用
### 全局设置
```
sqitch config --user user XXX
sqitch config --user user.email 'XXX'
```

### add database uri in sqitch.conf
```
sqitch init project --uri gitlab --engine pg
sqitch target add flipr_test db:postgres://user:password@localhost:5433/flipr_test
sqitch config core.pg.target flipr_test
```

