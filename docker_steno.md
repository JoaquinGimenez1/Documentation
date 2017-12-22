# Configure Docker Image to show AppCivist API doc

## 1. Install Docker-CE (Community Edition) 

SET UP THE REPOSITORY

1. Update the `apt` package index:
```bash
sudo apt-get update
``` 




```    

```

udo apt-get install     apt-transport-https     ca-certificates     curl     software-properties-common
    5  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    6  sudo apt-key fingerprint 0EBFCD88
    7  sudo add-apt-repository    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
    8  sudo apt-get update
    9  sudo apt-get install docker-ce
    
    sudo docker run hello-world
   12  clear
   13  git clone https://github.com/swagger-api/swagger-ui
   14  ls
   15  cd swagger-ui/
   
   
   23  vim dist/index.html 

### add las linea para que ordene! 



docker build -t swagger:1.1 --no-cache .


probar 

docker run -p 9000:8080 swagger:1.2

para que quede como deamon 

docker run -d -p 9000:8080 swagger:1.4

##


##
