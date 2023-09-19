<h3>초기설정</h3>

<li>한글 설정</li>

```
sudo apt-get install fonts-unfonts-core -y
sudo apt-get install ibus ibus-hangul -y
```

<li>파이썬 파일 실행</li>

```
<터미널 python 실행>
python [FILE_NAME]
```

<hr>

<h3>InfluxDB2 install</h3>
<li>InfluxDB download key using wget</li>

```
wget -q https://repos.influxdata.com/influxdata-archive_compat.key
echo '393e8779c89ac8d958f81f942f9ad7fb82a25e133faddaf92e15b16e6ac9ce4c influxdata-archive_compat.key' | sha256sum -c && cat influxdata-archive_compat.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg > /dev/null
echo 'deb [signed-by=/etc/apt/trusted.gpg.d/influxdata-archive_compat.gpg] https://repos.influxdata.com/debian stable main' | sudo tee /etc/apt/sources.list.d/influxdata.list
```

<li>Packages are up to date && install Influxdb2</li>

```
sudo apt-get update && sudo apt-get install influxdb2 -y
```

<li>InfluxDB as a background service on startup</li>

```
sudo service influxdb start
```

<li>InfluxDB is status (service)</li>

```
sudo service influxdb status
```

<hr>

<h3>Influx 명령어</h3>
<li>influx DB 접속</li>

```
sudo docker exec -it docker-influxdb-grafana bash
> influx
```

<li>DB 생성</li>

```
> create database testdb
> use testdb
```

<li>measurement insert</li>

```
> insert memory,host=server01,region=korea value=5.5
> insert memory,host=server02,region=japan value=4.5
```

<li>measurement 조회</li>

```
> show measurements

> select * from memory

> select "host", "time", "value" from memory where "host" = 'server01'

(컬럼명은 쌍따옴표, 조건문에 비교문자열은 홑따옴표)
```
 

<li>measurement insert(2)</li>

```
> insert memory,host=server03,name=alicek106 value=6.5
> select * from memory
```

<li>태그키 조회</li>

```
> show tag keys
> show field keys
```

<hr>

<h3>Grafana Istallation</h3>
<li>Repository의 GPG key를 더하기</li>

```
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

<li>Repository 더하기</li>

```
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

<li>프로그램 설치</li>

```
sudo apt update
sudo apt install grafana
```

<li>프로그램 실행</li>

```
sudo service grafana-server start
```

<li>influx import with python</li>

```
sudo pip3 install influxdb
```

