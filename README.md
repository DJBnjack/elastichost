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
sysctl -w vm.max_map_count=262144
```

## Edit Elastic jvm config
Add:
```
-Xms2g
-Xmx2g
```

## Run Elastic
```
cd elasticsearch-5.0.0-alpha5/bin
./elasticsearch
```
