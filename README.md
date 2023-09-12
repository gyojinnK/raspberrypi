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
