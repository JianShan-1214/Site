---
title: "Domjudge Docker 安裝流程"
date: 2021-08-01T01:35:00+08:00
slug: "domjudge-docker"
tags: ["雜學"]
---

Docker 安裝部份請自行上網查閱，建議使用 Linux 生態系統
Windows 部分需另外安裝 WSL

[docker hub](https://hub.docker.com/r/domjudge/domserver/)

[domjudge doc](https://www.domjudge.org/docs/manual/main/index.html)

### 第一步安裝`MariaDB`:
在`terminal`下
```shell 
docker run -it --name dj-mariadb -e MYSQL_ROOT_PASSWORD=rootpw -e MYSQL_USER=domjudge -e MYSQL_PASSWORD=djpw -e MYSQL_DATABASE=domjudge -p 13306:3306 mariadb --max-connections=1000 --max-allowed-packet=<MX_PACKET_SIZE> --innodb-log-file-size=<MX_LOG_SIZE>
```
* 參數部分建議都不需要動
* `<MX_PACKET_SIZE>`建議開最大測資大小的兩倍
* `<MX_LOG_SIZE>`建議開最大測資大小的十倍


### 第二步安裝`Domjudge Server`：
```shell
docker run --link dj-mariadb:mariadb -it -e MYSQL_HOST=mariadb -e MYSQL_USER=domjudge -e MYSQL_DATABASE=domjudge -e MYSQL_PASSWORD=djpw -e MYSQL_ROOT_PASSWORD=rootpw -e CONTAINER_TIMEZONE=Asia/Taipei -p 80:80 --name domserver domjudge/domserver:latest
```
* 如果有改密碼，記得要把對應的密碼改上去
* `CONTAINER_TIMEZONE`是時區的修改
* 使用`-p`參數可以設定 Port，左邊是 host 右邊是 container 的，官網預設 port 為 12345 這邊我把它改成 80
* 如果需要指定版本，可以把`latest`改成你需要的版本

以上步驟沒有問題就可以連到 [http://localhost/](http://localhost/) 看看有沒有什麼問題


admin 跟 judgehost 的密碼可以在 domserver 的 log 上看到
如果沒有可以下指令：
```shell
docker exec -it domserver cat /opt/domjudge/domserver/etc/initial_admin_password.secret
docker exec -it domserver cat /opt/domjudge/domserver/etc/restapi.secret
```
第一行是 admin 的密碼
第二行是 judgehost 的密碼


### 第三步安裝`JudgeHost`：
```shell 
docker run -it --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro --name judgehost-0 --link domserver:domserver --hostname judgedaemon-0 -e DAEMON_ID=0 -e CONTAINER_TIMEZONE=Asia/Taipei domjudge/judgehost:latest
```
* 如果剛剛有改版本的，這裡也要記得把`latest`改掉
* 有些可以手動新增的參數，只需要在前面加一個`-e`
    * `JUDGEDAEMON_USERNAME` 預設是`judgehost`，用於連到 API 的 username
    * `JUDGEDAEMON_PASSWORD` 預設是`password`，用於連到 API 的 password
* 如果需要多開，記得要換`--name`後面的參數，`DAEMON_ID`也要記得改，數字不能夠重複

以上`domjudge`就架設完成了

---

### 疑難排解
#### 找不到 Python
解決方式: chroot 進虛擬環境安裝 python3
```sh
chroot /chroot/domjudge
apt install -y python3
```
