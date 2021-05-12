### Download website

```
git clone https://github.com/Bramas/hotcrp-docker-compose
cd hotcrp-docker-compose
git checkout 1010aead376a7f4752f8ad128ad7cbcdae5175b6
git clone https://github.com/kohler/hotcrp app
cd app
git checkout 81c673edb4ae65a595a3a5b0ccab45d48d01eeaf
cd ../../
git clone https://chenju2k6@bitbucket.org/chenju2k6/hotcrp.git
cd hotcrp
tar xvf secret.tar.gz 
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
