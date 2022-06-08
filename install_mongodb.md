Install Document Database-MongoDB
===============================

## MongoDB

_MongoDB_ - is document-based open source database management system. The data is stored in a JSON-like format. This DBMS is highly available, scalable, and secure.

### Main features of MongoDB:
* It does not require a description of the table schema, as in relational databases. Data is stored as collections and documents.
* There are no complex JOINs between collections, as there are between relational database tables. Typically, the connection is made when saving data by merging documents.
* The data is stored in BSON format (binary JSON-like documents).
* Collections do not have to have a similar structure. One document may have one set of fields, while another document may have a completely different one (both type and number of fields).
* One document can have fields of different data types, the data does not need to be cast to the same type. The main advantage of MongoDB is that it can store any kind of data, but that data must be in JSON format.
![](https://innovationm.co/wp-content/uploads/2018/05/Akash_blog_image.png)
## Install MongoDB Community Edition on Ubuntu
**1. Import the public key used by the package management system.**
From a terminal, issue the following command to import the MongoDB public GPG Key 
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```
The operation should respond with an **OK.**

**However, if you receive an error indicating that gnupg is not installed, you can:**

1) Install gnupg and its required libraries using the following command:
```
sudo apt-get install gnupg
```
2) Once installed, retry importing the key:
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```
**2. Create a list file for MongoDB**

Create the list file _**/etc/apt/sources.list.d/mongodb-org-5.0.list**_ for your version of Ubuntu.

Click on the appropriate tab for your version of Ubuntu. If you are unsure of what Ubuntu version the host is running, open a terminal or shell on the host and execute _**lsb_release -dc**_

**The following instruction is for Ubuntu 20.04 (Focal).**
Create the _/etc/apt/sources.list.d/mongodb-org-5.0.list_ file for Ubuntu 20.04 (Focal):
```
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```
**3.Reload local package database.**

Issue the following command to reload the local package database:

```
sudo apt-get update
```

**4.Install the MongoDB packages.**

You can install either the latest stable version of MongoDB or a specific version of MongoDB.

To install the latest stable version, issue the following
```
sudo apt-get install -y mongodb-org
```
Optional. Although you can specify any available version of MongoDB, apt-get will upgrade the packages when a newer version becomes available. To prevent unintended upgrades, you can pin the package at the currently installed version:

```
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-database hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```
### Run MongoDB Community Edition

Init System

To run and manage your _mongod_ process, you will be using your operating system's built-in init system. Recent versions of Linux tend to use systemd (which uses the _systemctl_ command), while older versions of Linux tend to use **System V init** (which uses the _service_ command).

If you are unsure which init system your platform uses, run the following command:
```
ps --no-headers -o comm 1
```

Then select the appropriate tab below based on the result:

* `systemd` - select the **systemd (systemctl)** tab below.
* `init` - select the **System V Init (service)** tab below.

### 1) **Start MongoDB.**

You can start the _mongod_ process by issuing the following command:
```
sudo systemctl start mongod
```
If you receive an error similar to the following when starting mongod:

**_Failed to start mongod.service: Unit mongod.service not found._**

Run the following command first:
```
sudo systemctl daemon-reload
```
Then run the start command above again.

### 2) **Verify that MongoDB has started successfully.**
```
sudo systemctl status mongod
```
You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:
```
sudo systemctl enable mongod
```
### 3) **Stop MongoDB.**
As needed, you can stop the mongod process by issuing the following command:
```
sudo systemctl stop mongod
```
### 4) **Restart MongoDB.**
You can restart the mongod process by issuing the following command:
```
sudo systemctl restart mongod
```

You can follow the state of the process for errors or important messages by watching the output in the **_/var/log/mongodb/mongod.log_** file.

### 5) **Begin using MongoDB**

Start a _mongosh_ session on the same host machine as the mongod. You can run mongosh without any command-line options to connect to a mongod that is running on your localhost with default port 27017.
```
mongosh
```
> :information_source: For more information on connecting using mongosh, such as to connect to a mongod instance running on a different host and/or port, see the [<span style="color:yellow"> → mongosh documentation </span>](https://www.mongodb.com/docs/mongodb-shell/)

## **Install on Windows**
Available Downloads :
```
https://www.mongodb.com/try/download/community?tck=docs_server
```
Choose **Version,Platform, Package** and download.

