# ansible playbooks

```bash
# ansible-playbook --version
ansible-playbook 2.5.5
  python version = 3.7.0 (default, Aug 22 2018, 15:22:33) [Clang 9.1.0 (clang-902.0.39.2)]
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

