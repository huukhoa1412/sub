## Hướng dẫn chạy node
###### Cài đặt docker và cài đặt phần mềm hỗ trợ khác
```
#!/bin/bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl build-essential git wget jq make gcc ack tmux ncdu -y
sudo wget -qO /usr/local/bin/yq https://github.com/mikefarah/yq/releases/download/v4.27.3/yq_linux_amd64 && chmod +x /usr/local/bin/yq
apt update && apt install git sudo unzip wget -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
curl -SL https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```
### Tạo ví trong lệnh Linux
```
wget -O create-subspace-wallet.sh https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/create-subspace-wallet.sh
chmod +x create-subspace-wallet.sh
./create-subspace-wallet.sh
```

### Cài đặt tự động
```
# You need to create the rewardaddress first, read above, if your PC have 8 cores then fill with 8 to create 8 addresses
# 1 node need 1 CPU core, 2GB RAM and 10GB SSD, DYOR

wget -O subspace-auto-install.sh https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/subspace-auto-install.sh
chmod +x subspace-auto-install.sh
./subspace-auto-install.sh

# This script use port ranges 4000 5000 6000, if you want to change the range, open script and edit it
# And you must open firewall or NAT by yourself
```


### Cài tay
###### Tạo thư mục và chép 2 file docker-compose.yaml + .env vào thư mục folder mới tạo
```
cd $HOME
mkdir node1
cd node1
wget -O docker-compose.yaml https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/docker-compose.yaml
wget -O .env https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/.env
```
### Bạn có thể kiểm tra cổng nào bạn đang sử dụng bằng lệnh này
```
lsof -i -P -n | grep LISTEN
```
#### Sau khi tải xong, bạn cần thay đổi biến bên trong tệp .env
#### Mỗi tệp .env phải là một cổng port khác, tên nút node khác, địa chỉ phần thưởng reward khác
```
nano .env
```
###### Một số lệnh
###### Chạy 1 node
```
docker compose up -d
```
###### Hiển thị tất cả docker đang chạy
```
docker ps
```
###### Xem logs
```
docker compose logs -f --tail=100 | grep <container-name>
```
###### Dừng 1 node
```
docker compose down
```

### Nếu bạn muốn chạy node thứ hai hoặc node n, chỉ cần thay đổi mã ở đây, node2 --> noden
```
cd $HOME
mkdir node2
cd node2
wget -O docker-compose.yaml https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/docker-compose.yaml
wget -O .env https://raw.githubusercontent.com/huukhoa1412/sub/main/subspace/.env

Change ports, nodename, reward address inside .env file
nano .env

docker compose up -d
```
