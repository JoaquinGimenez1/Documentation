# How To Install and Configure AppCivist Pb Client on Ubuntu 16.04

## Introduction
This guide explains step by step how to download and install a production instance of the Web Client of AppCivist, for the instance of Participatory Budgeting.

## Install

First we update all the system.

```
sudo apt-get update
sudo apt-get -y upgrade
sudo apt -y full-upgrade
```

> Optional but recommended, next step will install essentials tools for developers.


```
sudo apt-get install -y build-essential
```

Next step will install **node.js V6**.

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

Using NPM, install Bower package manager

```
npm install -g bower
```

Install Grunt

````
npm install -g grunt
```


Install the CSS authoring framework Compass (you will need Ruby first)

```
sudo apt-get install -y ruby ruby-dev ruby-haml
gem update --system
gem install compass   
```

Install the Sass language

```
gem install sass
```

Clone the repository

```
git clone https://github.com/socialappslab/appcivist-pb-client.git
```

You need to download the dependencies before run the application 

```
cd appcivist-pb-client/
npm install
```

Now you can run the app typing

`grunt server
