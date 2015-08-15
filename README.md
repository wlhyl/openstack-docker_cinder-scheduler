# 环境变量
- CINDER_DB: cinder数据库ip
- CINDER_DBPASS: cinder数据库密码
- RABBIT_HOST: rabbitmq IP
- RABBIT_USERID: rabbitmq user
- RABBIT_PASSWORD: rabbitmq user 的 password
- KEYSTONE_INTERNAL_ENDPOINT: keystone internal endpoint
- KEYSTONE_ADMIN_ENDPOINT: keystone admin endpoint
- CINDER_PASS: openstack cinder用户密码
- MY_IP: my_ip
# volumes:
- /opt/openstack/cinder-scheduler/: /etc/cinder-scheduler
- /opt/openstack/log/cinder-scheduler/: /var/log/cinder-scheduler/

# 启动cinder-scheduler
```bash
docker run -d --name cinder-scheduler \
    -v /opt/openstack/cinder-scheduler/:/etc/cinder \
    -v /opt/openstack/log/cinder-scheduler/:/var/log/cinder/ \
    -e CINDER_DB=10.64.0.52 \
    -e CINDER_DBPASS=cinder_dbpass \
    -e RABBIT_HOST=10.64.0.52 \
    -e RABBIT_USERID=openstack \
    -e RABBIT_PASSWORD=openstack \
    -e KEYSTONE_INTERNAL_ENDPOINT=10.64.0.52 \
    -e KEYSTONE_ADMIN_ENDPOINT=10.64.0.52 \
    -e CINDER_PASS=cinder \
    -e MY_IP=10.64.0.52 \
    10.64.0.50:5000/lzh/cinder-api:kilo
```