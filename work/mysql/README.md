# 主从设置

- 进入写数据库

  > docker exec -it all.mysql.writer sh

  ```sql
  # 查看 master 状态
  mysql> show master status;

  # 记录 File 和 Position 的值
  binlog.000004 158
  ```

- 写入读数据库 1

  > docker exec -it all.mysql.reader1 sh

  ```sql
  # 配置主从关系
  mysql> change master to master_host='127.0.0.1',master_port=13306,master_user='root',master_password='123456',master_log_file='binlog.000004',master_log_pos=158

  # 启动同步
  mysql> start slave;

  # 查看状态
  mysql> show slave status;


  ```
