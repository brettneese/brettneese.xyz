Category: Quick Tips
Date: 2019/08/21
Tags: devops

# Installing K6/Grafana/Influx DB on Ubuntu

[K6](https://k6.io/) is a great load-testing tool that can spit reports out to Grafana via InfluxDB. To install the full stack on a full-stack Ubuntu instance, run something like: 

```shell
curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -
source /etc/lsb-release
echo "deb https://repos.influxdata.com/${DISTRIB_ID,,} ${DISTRIB_CODENAME} stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
sudo apt-get update && sudo apt-get install influxdb
sudo systemctl unmask influxdb.service
sudo systemctl start influxdb
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
sudo /bin/systemctl daemon-reload
sudo /bin/systemctl enable grafana-server
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 379CE192D401AB61
echo "deb https://dl.bintray.com/loadimpact/deb stable main" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install k6
sudo apt-get install node.js npm
```

The default Grafana username and password is "admin/admin," but it'll prompt you to change them on first login.