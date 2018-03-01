# Sqitch使用
## 特点
- Migration
 - Incomplete mini-language
 - No logical replication integration
 - Numbered scripts hard to track
 - No VCS awareness

- why sqitch
 - No opinions
 - Native scripting (psql, sqlite3, SQL*Plus)
 - Cross-project dependency resolution
 - Distribution bundling
 - Integrated verification testing
 - No numbering
 - Reliable sequential deployment ordering

- Feature
 - Reduced duplication
 - Built-in configuration
 - Iterative development
 - Targeted deployment
 - Git-style interface
 - Deployment tagging  
 
## 使用
## 查看
```
ps_lscluster
sudo serive postgresql start
```
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

### 常见命令
```
rebase
rework
add -r -n 
revert --to 
log
show change @HEAD
status
bundle
tag
config
```