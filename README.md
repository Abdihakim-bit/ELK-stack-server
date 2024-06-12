# ELK-stack-server
This guide covers the complete setup of an ELK (Elasticsearch, Logstash, and Kibana) server, configuring Filebeat to send logs from a LAMP web server to Logstash, and visualizing these logs in Kibana.
## Prerequisites

- Ubuntu server with adequate resources (16GB of RAM recommended)
- Root or sudo access

## Installation Steps

### 1. Install Elasticsearch

```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
sudo apt-get update && sudo apt-get install elasticsearch
```

### 2. Install Logstash

```bash
sudo apt-get update && sudo apt-get install logstash
```

### 3. Install Kibana

```bash
sudo apt-get install kibana
```

### 4. Install Filebeat on the LAMP web server

```bash
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.14.0-amd64.deb
sudo dpkg -i filebeat-8.14.0-amd64.deb
```
## Configuration

## Start the ELK stack

```bash
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl start logstash
sudo systemctl enable logstash
sudo systemctl start kibana 
sudo systemctl enable kibana
```
