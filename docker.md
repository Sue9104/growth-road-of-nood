# docker

教程：https://www.gitbook.com/book/yeasy/docker_practice/details

## 三剑客
- machine：　创建虚拟化环境
- compose：任务编排，支持多个应用
- swarm: 集群（create join manage）

## 相关命令
```
docker node ls 查看集群节点信息
docker service create --replicas 4　创建单集群docker服务
docker stack deploy -c docker-compose.yml deploy-demo　部署多个集群服务
```