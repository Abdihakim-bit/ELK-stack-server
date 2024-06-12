# ELK-stack-server
This guide covers the complete setup of an ELK (Elasticsearch, Logstash, and Kibana) server, configuring Filebeat to send logs from a LAMP web server to Logstash, and visualizing these logs in Kibana.
## Prerequisites

- Ubuntu server with adequate resources (16GB of RAM recommended)
- Root or sudo access

## Installation Steps


### 1. Install Filebeat on the LAMP web server

```bash
curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-8.14.0-amd64.deb
sudo dpkg -i filebeat-8.14.0-amd64.deb
```
### 2. Install Elasticsearch on the ELK server

```bash
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
sudo apt-get install apt-transport-https
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
sudo apt-get update && sudo apt-get install elasticsearch
```

### 3. Install Logstash on the ELK server

```bash
sudo apt-get update && sudo apt-get install logstash
```

### 4. Install Kibana on the ELK server

```bash
sudo apt-get install kibana
```

## Configurations

### 1. Filebeat Configuration on LAMP Web Server

- Configure filebeat on the LAMP web server to send the logs in json format to Logstash. Refer to [filebeat.yml](https://github.com/Abdihakim-bit/ELK-stack-server/blob/main/filebeat.yml) for an example.
  
### 2. Logstash Configuration on ELK Server

 - Configure Logstash to accept, process and send the results to Elasticsearch. Refer to [logstash.conf](https://github.com/Abdihakim-bit/ELK-stack-server/blob/main/logstash.conf) for an example.

### 3. Elasticsearch Configuration

 - Elasticsearch typically requires minimal configuration for basic setups. However, depending on your requirements, you may need to adjust settings such as memory allocation and cluster configuration.

### 4. Kibana Configuration

 - Kibana's configuration usually involves specifying Elasticsearch's URL and other settings. You can adjust these configurations in the kibana.yml file.

## Start the ELK stack
- Ensure all ELK components are started and enabled to run on system boot:
```bash
sudo systemctl start elasticsearch
sudo systemctl enable elasticsearch
sudo systemctl start logstash
sudo systemctl enable logstash
sudo systemctl start kibana 
sudo systemctl enable kibana
```
