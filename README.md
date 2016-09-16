# elastichost
Scripts to run on the elastichost

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
0.0.0.0
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
