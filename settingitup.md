---
layout: page
title: Setting it up
permalink: /settingitup/
---
Setting it up

## Web service Installation
Before installing make sure that you have included a conf.py file in the docs/ path. There is an example under docs/conf_template.py. You can copy and edit that file in order to install your local RO2SHARE.
### Requirements
You will need to have a SPARQL Endpoint (e.g. Fuseki Triple Store) up and running in order to run this web service.

- Download Apache Fuseki from the [Apache Downloads Web site](https://jena.apache.org/download/#jena-fuseki)
- Uncompress it
```bash
cd apache-jena-fuseki-3.4.0/
./fuseki-server
```
The go to http://localhost:3030 and create a new dataset called 'ro2share'.
### Using Virtual Enviroment
```bash
sudo apt-get update -y
sudo apt-get install -y python-pip python-dev build-essential libxml2-dev libxslt1-dev zlib1g-dev
git clone https://github.com/LinkingDataIO/RO2SHARE.git
cd RO2SHARE
virtualenv .env
source .env/bin/activate
pip install -r requirements.txt
python run.py
```

### Using the Dockerfile
Replace the 'localhost' reference in the SPARQL\_QUERY\_ENDPOINT and SPARQL\_UPLOAD\_ENDPOINT values  in your docs/conf.py with the IP Address of your Docker Host corresponding to the Network Interface docker0.

```bash
git clone https://github.com/LinkingDataIO/RO2SHARE.git
cd RO2SHARE
sudo docker build -t username:RO2SHARE .
sudo docker run -p 8080:8080 -v /tmp:/tmp username:RO2SHARE
```
## Client Installation
The client is available at [LinkingDataIO/RO2SHARE-client](https://github.com/LinkingDataIO/RO2SHARE-client). Clone it and Include your ORCID APP Client ID in src/environments/enviroment.ts and src/environments/enviroment.prod.ts

### Using NPM
```bash
git clone https://github.com/LinkingDataIO/RO2SHARE-client.git
cd RO2SHARE-client
npm install
npm start
```

### Using Dockerfile
```bash
git clone https://github.com/LinkingDataIO/RO2SHARE-client.git
cd RO2SHARE-client
sudo docker build -t username:RO2SHARE-client .
sudo docker run -p 4200:4200 -v /tmp:/tmp username:RO2SHARE-client
```

