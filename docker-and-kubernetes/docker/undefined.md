# 설치

* Linux Ubuntu 22.04

```bash
curl -sSL https://get.docker.com/ | sh
sudo systemctl start

sudo gpasswd -a dockerName docker
# 또는 
sudo usermod -aG docker dockerName
# 실행 후 다시 로그인
```

* [https://docs.docker.com/engine/install/debian/#install-using-the-repository ](https://docs.docker.com/engine/install/debian/#install-using-the-repository)치

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# docker engine
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

* 설치 확인

```bash
docker --version
# 또는
docker info | head
```









