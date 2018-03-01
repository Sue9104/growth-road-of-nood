# Sqitch使用

## sqitch
### 全局设置
```
sqitch config --user user XXX
sqitch config --user user.email 'XXX'
```

### add database uri in sqitch.conf
```
sqitch target add flipr_test db:postgres://user:password@localhost:5433/flipr_test

```