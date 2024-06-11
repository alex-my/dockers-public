# windows 下便捷使用 docker

# 额外操作

执行 `docker-compose up -d` 后需要额外执行一些命令

## mysql

- 进入`writer`节点

  ```shell
  docker exec -it all.mysql.writer sh
  ```

- 创建同步用户`reader`

  ```sql
  CREATE USER 'reader'@'%' IDENTIFIED BY '123456';
  GRANT REPLICATION SLAVE ON *.* TO 'reader'@'%' IDENTIFIED BY '123456';

  ```
