### What is this? ###

This is a fork from Bramas's repository. Check Readme.md.orig for the original README. It setups a hotcrp application using 4 docker containers. I modified the mailserver part to enable Emails sending from a Google Cloud VM instance thourgh SendGrid.  

### Dependencies ###

This application should be run on any system that run docker. I've tested it on MacOs, Linux and Google's customized OS running on Google Cloud Compute Engine (container optimized image)

### Download website

```
git clone https://github.com/chenju2k6/hotcrp-docker-compose
cd hotcrp-docker-compose
#git checkout 1010aead376a7f4752f8ad128ad7cbcdae5175b6
git clone https://github.com/kohler/hotcrp app
cd app
git checkout 81c673edb4ae65a595a3a5b0ccab45d48d01eeaf
cd ../../
```

### Override docker 

```
cd hotcrp-docker-compose/docker
rm -rf *
cp ../../hotcrp/docker/* .
```

### Override docker-compose.xml

```
cp hotcrp/docker-compose.xml .
```


### Override .env

```
cp hotcrp/env .env
```

### copy mailenv

```
cp hotcrp/mailserver.env .
```

### Now should able to start the website

```
docker-compose up -d
```


### Get mail tool and add Email ###

```
wget https://raw.githubusercontent.com/docker-mailserver/docker-mailserver/v9.0.1/setup.sh
chmod a+x setup.sh
./setup.sh email add hotcrp@submit.acsac.org
```

### Setup forwarding ###

```
cp hotcrp/forward .
docker-compose up -d
```


### Enable SSL ###

Change default.conf with SSL
Add certificates
Change port to 443
