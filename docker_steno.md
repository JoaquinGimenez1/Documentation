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
Search the following script

```js
// Build a system
  const ui = SwaggerUIBundle({
    url: "http://petstore.swagger.io/v2/swagger.json",
    dom_id: '#swagger-ui',
    deepLinking: true,
    presets: [
      SwaggerUIBundle.presets.apis,
      SwaggerUIStandalonePreset
    ],
    plugins: [
      SwaggerUIBundle.plugins.DownloadUrl
    ],
    layout: "StandaloneLayout"
  })
```

We need yo change the url to point AppCivist Doc and add the folowing parameters to sort

```js
// Build a system
  const ui = SwaggerUIBundle({
    url: "https://platform.appcivist.org/api/doc.json",  //AppCivist URL
    dom_id: '#swagger-ui',
    deepLinking: true,
    operationsSorter: 'method',   //NEW LINE
    tagsSorter: 'alpha',          //NEW LINE
    presets: [
      SwaggerUIBundle.presets.apis,
      SwaggerUIStandalonePreset
    ],
    plugins: [
      SwaggerUIBundle.plugins.DownloadUrl
    ],
    layout: "StandaloneLayout"
  })
```
Save and exit the file

The next step is to build the docker image

```bash
docker build -t swagger-ui-sorted:lastest --no-cache .
```
Check the image just builded typing 

```bash
docker ps
```
To test the Docker Image we can type
```bash
docker run -p 9000:8080 swagger:1.2
```

probar 

docker run -p 9000:8080 swagger:1.2

para que quede como deamon 

docker run -d -p 9000:8080 swagger:1.4

