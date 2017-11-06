# How To Install and Configure AppCivist Platform on Ubuntu 16.04

## Introduction
This guide explains step by step how to download and install the AppCivist Core Platform and the AppCivist database on a Ubuntu 16.04 server.

The AppCivist Core Platform provides a RESTful API implemented with the full-stack Playframework. Follow these instructions to download the source code and run it.

## Installation

`sudo apt-get update`

`sudo apt-get -y upgrade`

`sudo apt -y full-upgrade`

`sudo apt-get install -y default-jdk`

> Optional but recommended, will install build-essential.


`sudo apt-get install -y build-essential`

> Optional but recommended, will install node.js V6.


`curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`

`sudo apt-get install -y nodejs`


Now we install PostgreSQL

`sudo apt-get install postgresql postgresql-contrib`

`systemctl start postgresql`

`systemctl enable postgresql`

We have to modify the file `pg_hba.conf` to support password login

> The directory will differ depending on psql version installed


`vim /etc/postgresql/9.5/main/pg_hba.conf`

Search for the line with, and change 

`local   all             all                                     peer`

To

`local   all             all                                     md5`

Then restart psql server

`sudo service postgresql restart`

Make sure you are on the home directory of your user.

`cd`

Now we can clone the repository

`git clone https://github.com/socialappslab/appcivist-platform.git`

`cd appcivist-platform/`

Copy the sql script into postgres home directory

`cp conf/sql/database-create-postgres.sql /var/lib/postgresql/`

Login into postgres 

`sudo -i -u postgres`

Login psql console

`psql`

Create the database with default name

`create database appcivistcore;`

Create password for database user `postgres`

`\password`

Exit psql console

`\q`

Run the sql script into appcivistcore database


`psql -d appcivistcore -f database-create-postgres.sql`

Logout from postgres

`logout`

Install Activator from compiled source code

> Next step may take a long time to complete. This will install all dependecies required by Play-Framework


Make sure you are on the home directory of your user.

`cd`

`cd appcivist-platform/`

`sudo ./activator`

Once finished you will see

`[appcivist-core] $ `

Then type 

`exit`

Copy the next files 

`cp conf/local.sample.conf conf/local.conf`

`cp conf/local.sample.conf conf/local.test.conf`
 
`cp conf/local.logback.sample.xml conf/local.logback.xml`
 
`cp conf/play-authenticate/mine.conf.sample conf/play-authenticate/mine.local.conf`

`cp conf/play-authenticate/smtp.conf.sample conf/play-authenticate/smtp.local.conf`

Change email address on the next files

smtp.local



Run the server using the following commands

`./activator`

`run -Dconfig.resource=local.conf -Dlogger.file=conf/local.logback.xml`

On your browser, go to 

http://localhost:9000/api/doc 

To visit the documentation of the API endpoints and have try them out with real examples.





