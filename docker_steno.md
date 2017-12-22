# Configure Docker Image to show AppCivist API doc

## 1. Install Docker-CE (Community Edition) 
Official Documentation: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

## 2. Configure Swagger-UI

Clone the repository typing:
```bash
git clone https://github.com/swagger-api/swagger-ui
cd swagger-ui/
```
We need to add some parameters to sort the methods
```bash
vim dist/index.html 
```



### add las linea para que ordene! 



docker build -t swagger:1.1 --no-cache .


probar 

docker run -p 9000:8080 swagger:1.2

para que quede como deamon 

docker run -d -p 9000:8080 swagger:1.4

##


##
