```
- tạo 1 hard disk khác vào trong server và lưu dữ liệu vào ổ cứng này (backup and rollback)
- hard disk > add > hard disk > Recommend > 20gb > success

SSH
sudo mkfs.ext4 -m 0 /dev/sdb
mkdir /data
echo "/dev/sdb  /data  ext4  defaults  0  0" | sudo tee -a /etc/fstab
mount -a
sudo df -h

apt update
apt install docker.io
apt install docker-compose

version: '3'
services:
  rancher-server:
    image: rancher/rancher:v2.9.2
    container_name: rancher-server
    restart: unless-stopped
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - /data/rancher/data:/var/lib/rancher
    privileged: true

# docker compose up -d
# https://192.168.1.114/

```
