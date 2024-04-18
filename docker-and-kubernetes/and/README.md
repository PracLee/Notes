# 명령어 & 사용법

* Docker 에서 사용가능한 Linux 기술
  *   namespace

      \-> cgroup, mnt, pid, net, ipc, uts, user(UID), time
  * cgroup
  * Union filesystem

{% code title="namespace" fullWidth="false" %}
```bash
# mount namespace 격리
sudo unshare -m bash
# bash PID namespace 격리
sudo unshare --fork --pid bash
# PID namespace 격리 및 proc 파일 시스템 마운트
sudo unshare --fork --pid --mount-proc bash
# uts namespace 와 hostname 격리
sudo unshare -u bash
```
{% endcode %}

{% code title="croup" %}
```bash
# systemd 를 이용한 Cgroup 제어 (sleep)
sudo systemd-run --unit=myunit sleep 1000
# cgroup을 이용한 docker container 제어
docker run --rm -it --name containerName imageNmae bash
# M1 Mac과 같이 CPU infra가 다른 경우의 container 제어
docker run --rm -itd --name containerName --platform linux/amd64 imageNmae
```
{% endcode %}
