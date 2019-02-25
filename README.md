# ansible playbooks

```bash
# ansible-playbook --version
ansible-playbook 2.7.7
  python version = 3.7.0 (default, Aug 22 2018, 15:22:33) [Clang 9.1.0 (clang-902.0.39.2)]
```

## parted disks

`inventory.hosts`

```ini
[redis]
your_hosts
```

编辑 `roles/redis/vars/custom.yml` , 设置磁盘和对应的挂载路径。 字典格式

```yml
disks:
  /dev/vdb: /data
  # /dev/vdc: /data1

## ACTION 表示对磁盘进行的动作
# + present : parted and mount
# + absent : unmount and delete
# + info :  查看当前信息
ACTION: info
```

+ 执行安装
```bash
# way1
## 编辑 custom.yml
ansible-playbook -i inventory.hosts parted_disks.yml

### or
ansible-playbook -i inventory.hosts parted_disks.yml -e "ACTION=[info|absent|present]"
```


## java

install oracle jdk

## redis

`inventory.hosts`

```ini
[redis]
your_hosts
```

+ 执行安装
```bash
# way1
## 编辑 `roles/redis/vars/custom.yml` ,设置安装版本和 SHA 校验
ansible-playbook -i inventory.hosts redis.yml

### or
ansible-playbook -i inventory.hosts redis.yml -e "REDIS_VERSION=5.0.2" -e "REDIS_DOWNLOAD_SHA=xxxxxx"
```


## docker

```bash
ansible-playbook -i inventory.hosts docker.yml
```