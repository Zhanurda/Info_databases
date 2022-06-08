## **How to Install Elasticsearch on Ubuntu**
**Elasticsearch** is a platform used for real-time full-text searches in applications where a large amount of data needs to be analyzed. In combination with other tools, such as Kibana, Logstash, X-Pack, etc., Elasticsearch can aggregate and monitor Big Data at a massive scale.

With its RESTful API support, you can easily manage your data using the common HTTP method. Due to its speed and ease of use, it also became suitable for more complex tasks that Hadoop and Spark handle.

**Add Elasticsearch Repository**

First, update the GPG key for the Elasticsearch repository.

Use the **wget** command to pull the public key:

```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
The output should display **OK** if everything went as it should.
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/gpg-key-add.png)

:bulb: Note: You need to type the above command exactly as it is written in the example. Make sure you use uppercase letters and spaces appropriately. Also, do not forget to add a dash at the end of the command.

Next, use this command to add the repository to your system.

```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
```

**Install Elasticsearch**
Finally, it is time to install Elasticsearch.

Update the package index one more time before proceeding.
```
sudo apt update
```

Then, run the installation:
```
sudo apt install elasticsearch
```
:information_source: The package is around 300MB. Let the system download the archive and finish the installation.
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/1_install-elasticsearch.png)

**Start Elasticsearch Service**

Once the installation is finished, Elasticsearch does not run until you start it. Also, when you reboot the machine, you need to rerun the Elasticsearch service as it does not start automatically.

To have Elasticsearch automatically reload when the system restarts, use the following commands:

First, reload the systemd configuration:
```
sudo systemctl daemon-reload
```

Then, enable the Elasticsearch service with:
```
sudo systemctl enable elasticsearch.service
```
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/enable-elasticsearch-service.png)

And finally, after the service is enabled, start Elasticsearch:
```
sudo systemctl start elasticsearch.service
```

:information_source: Note: If you're on Windows Ubuntu, the systemctl commands won't work. Instead, use the following commands to start, stop and restart the Elasticsearch service:
```
sudo service elasticsearch start
sudo service elasticsearch stop
sudo service elasticsearch restart
```
Let the process complete. It may take a few moments. There will be no specific response from the terminal.

Now, Elasticsearch will start every time you turn on or reboot the system.

If you make changes to configuration files, or need to restart Elasticsearch for any reason, use:
```
sudo systemctl restart elasticsearch.service
```
When you need to stop the service, use the following command:
```
sudo systemctl stop elasticsearch.service
```

:information_source: Note: Elasticsearch is just one component of the Elastic (ELK) stack. Follow our guide to install the ELK stack on Ubuntu.

**Check Elasticsearch Status**

Once you finish using the commands to start, restart, and stop Elasticsearch, you can also check the status of the service.

To do so, enter:
```
service elasticsearch status
```
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/elasticsearch-status.png)


## **Install on Windows**
Download and unzip Elasticsearch
```
https://www.elastic.co/downloads/elasticsearch
```