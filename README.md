# Elasticsearch
Setup of Elasticsearch

## Install JAVA
```sudo apt-get install default-jre -y```

## Install Elastic
```
curl -L -O https://download.elastic.co/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/5.0.0-alpha5/elasticsearch-5.0.0-alpha5.tar.gz
tar -xvf elasticsearch-5.0.0-alpha5.tar.gz
```

## Setup Java options
```
sudo sysctl -w vm.max_map_count=262144
sudo sysctl -w fs.file-max=100000
```

## Edit Elastic jvm config
```
nano elasticsearch-5.0.0-alpha5/config/jvm.options
```

Add:
```
-Xms2g
-Xmx2g
```

## Edit Elastic config
```
nano elasticsearch-5.0.0-alpha5/config/elasticsearch.yml
```

Set bind address to:
```
network.host: 0.0.0.0
```

Set amount of master nodes:
```
discovery.zen.minimum_master_nodes: 1
```

## Run Elastic
```
cd elasticsearch-5.0.0-alpha5/bin
./elasticsearch
```

# Kibana
Setup to run for Kibana

## Download and unzip
```
curl -L -O https://download.elastic.co/kibana/kibana/kibana-5.0.0-alpha5-linux-x86_64.tar.gz
tar -xvf kibana-5.0.0-alpha5-linux-x86_64.tar.gz
```

## Edit config to bind to 0.0.0.0
```
nano kibana-5.0.0-alpha5-linux-x86_64/config/kibana.yml
```

## Run Kibana
```
cd kibana-5.0.0-alpha5-linux-x86_64/bin/
./kibana
```

# Logstash

## Download and unpack
```
curl -L -O https://download.elastic.co/logstash/logstash/logstash-5.0.0-alpha5.tar.gz
tar -xvf logstash-5.0.0-alpha5.tar.gz
```

## Create logstash.conf
```
nano logstash.conf
```
Use this content:
```
input {
  gelf {}
}
output {
  elasticsearch { }
  stdout { }
}
```

## Run Logstash
```
logstash-5.0.0-alpha5/bin/logstash -f logstash.conf
```
