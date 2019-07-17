# Readme

## 私有仓库指向

vim /etc/systemd/system/multi-user.target.wants/docker.service
```
ExecStart=/usr/bin/dockerd --storage-opt dm.loopdatasize=2000G --storage-opt dm.loopmetadatasize=10G --storage-opt dm.fs=ext4 --storage-opt dm.basesize=100G --insecure-registry 192.168.126.100:5000
```
systemctl daemon-reload
systemctl restart docker.service

由于我已经映射5000端口到宿主机，所有这里使用"192.168.126.100:5000"，另外如果不做这步，就需要私有仓库增加ssl支持。

## 管理

管理访问：http://192.168.126.100:8080

初始用户和密码: admin/admin

建议给admin添加角色授权，UI_DELETE、write-all 。

## 使用

```
docker login 192.168.126.100:5000

```
提示输入，admin/admin。
登录成功后就可以正常使用私有源了。注意拉取也需要登录。
