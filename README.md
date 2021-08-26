# Test API Apps

Juiceshop: https://github.com/bkimminich/juice-shop
Run locally with:
```
docker pull bkimminich/juice-shop
docker run --rm -p 3000:3000 bkimminich/juice-shop
```
Runs on port 3000

=============

Httpbin: https://httpbin.org/#/
Run locally with:
```
docker run -p 4000:80 kennethreitz/httpbin
```
Runs on port 4000

=============

vAmPI: https://github.com/erev0s/VAmPI
openapi spec: https://raw.githubusercontent.com/erev0s/VAmPI/master/openapi_specs/openapi3.yml
Run locally with:
```
git clone https://github.com/erev0s/VAmPI
cd VAmPI
sudo apt install python3-pip
pip3 install -r requirements.txt
python3 app.py &
```
Runs on port 5000

=============

Sockshop: https://microservices-demo.github.io/
Run locally with:
```
git clone https://github.com/microservices-demo/microservices-demo
cd microservices-demo
docker-compose -f deploy/docker-compose/docker-compose.yml up -d
```

=============

MS conference demo: https://conferenceapi.azurewebsites.net?format=json
Can be imported into APIM through openapi spec
Doc: https://docs.microsoft.com/en-us/azure/api-management/import-and-publish

=============

crAPI: https://github.com/OWASP/crAPI
Run locally with:
```
sudo apt update
sudo apt install docker.io -y
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod 755 /usr/local/bin/docker-compose
git clone https://github.com/OWASP/crAPI
cd crAPI
git branch
git checkout main
# There is a bug in the latest alpine 3.14, so edit Dockerfile in services/workshop folder 
# and replace python:3.8-alpine with python:3.8-alpine3.13 on lines 16 and 38
sudo deploy/docker/build-all.sh
# in deploy/docker/docker-compose.yml change crapi-web port to "0.0.0.0:8888:80" and set mailhog port to 
"0.0.0.0:8025:8025" because by default they are listening on localhost
sudo docker-compose -f deploy/docker/docker-compose.yml --compatibility up -d
http://<crapi-vm-ip>:8888
```
Runs on port 8888

Scripts have been written to hit the crAPI API with vulnerabilities. It requires the requests python module which can be installed as follows:
```
sudo apt install python-pip -y
pip install requests
```

They need to be run from another VM to make sure that linux-mirroring works on the crAPI VM. The script run-all.sh runs all the python sub-scripts with a 5 sec delay in between. Change the file config.py to reflect the IP/FQDN, port and path-suffix of the crAPI VM.

=============

vAPI: https://github.com/mattvaldes/vulnerable-api
Blog post with info: https://badshah.io/writeup/vulnerable-api/

Run locally with:
```
docker run -tid -p 8081:8081 --name api mkam/vulnerable-api-demo
```
Runs on port 8081

==============

Mockbin: https://mockbin.com/
