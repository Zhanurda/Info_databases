## **How to Install Cassandra on Ubuntu**
**Apache Cassandra** is a popular, open-source NoSQL database software. It provides high availability while handling a large amount of data. Regular relational databases cannot handle linear scaling, seamless data distribution, and other big data requirements as efficient as Cassandra.

A number of big players in online industries have turned to Apache Cassandra. Some of them include Netflix, Apple, Uber, and eBay.

### **Add Apache Cassandra Repository and Import GPG Key**

You need to add the Apache Cassandra repository and pull the GPG key before installing the database.

Enter the command below to add the Cassandra repository to the sources list:

```
sudo sh -c 'echo "deb http://www.apache.org/dist/cassandra/debian 40x main" > /etc/apt/sources.list.d/cassandra.list'
```
The output returns to a new line with no message.

The last major Cassandra release at the time of writing this article is 4.0. That is why we used 40 in the command. To install an older version, for example 3.9, replace 40x with 39x.

Then, use the wget command to pull the public key from the URL below:
```
wget -q -O - https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add -
```
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/add-gpg-cassandra.png)

If you entered the command and the URL correctly, the output prints **OK**.

:information_source: **Note:** pay attention the letter case in the URL above. You need to enter the correct case and the dash at the end of the command.

## **Install Apache Cassandra**
You are now ready to install Cassandra on Ubuntu.

Update the repository package list:
```
sudo apt update
```
Then, run the install command:
```
sudo apt install Cassandra
```
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/install-cassandra.png)

:information_source: **Note:** Once the installation finishes, the Cassandra service starts automatically. Also, a user cassandra is created during the process. That user is used to run the service.

## **Verify Apache Cassandra Installation**

Finally, to make sure the Cassandra installation process completed properly, check cluster status:
```
nodetool status
```
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/nodetool-cassandra.png)

The UN letters in the output signal that the cluster is working.

You can also check Cassandra status by entering:
```
sudo systemctl status cassandra
```

The output should display **active (running)** in green.
![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/cassandra-status.png)

## **Commands to Start, Stop, and Restart Cassandra Service**

If, for any reason, the service shows inactive after the installation, you can start it manually.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/cassandra-inactive.png)

Use the following command to start Cassandra:
```
sudo systemctl start cassandra
```

Check the status of the service again. It should change to active.

To restart the service, use the **restart** command:

```
sudo systemctl restart cassandra
```

To stop the Cassandra service, enter:
```
sudo systemctl stop cassandra
```
The status shows **inactive** after using the **stop** command.

## **Optional: Start Apache Cassandra Service Automatically on Boot**

When you turn off or reboot your system, the Cassandra service switches to inactive.

To start Cassandra automatically after booting up, use the following command:
```
sudo systemctl enable cassandra
```

Now, if your system reboots, the Cassandra service is enabled automatically.


## **Install Cassandra on Windows**

**Install and Configure Python 2.7 on Windows**

Users interact with the Cassandra database by utilizing the cqlsh bash shell. You need to install Python 2.7 for cqlsh to handle user requests properly.

Install Python 2.7 on Windows

1. Visit [<span > the Python official download  page </span>](https://www.python.org/downloads/release/python-2718/) and select the Windows x64 version link.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/select-python-windows-x64-version-executable.png)

2. Define if you would like Python to be available to all users on this machine or just for your user account and select **Next.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/python-2.7-installation-windows-cassandra.png)

3. Specify and take note of the Python installation folder location. Feel free to leave the default location **C:Python27** by clicking **Next.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/select-python-installation-directory-windows.png)

4. The following step allows you to customize the Python installation package. Select **Next** to continue the installation using the default settings.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/select-python-installation-options-windows.png)

5. The installation process takes a few moments. Once it is complete, select **Finish** to conclude the installation process.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/python-2.7-finish-installation-windows.png)

## Edit Environment Variable for Python 2.7

1. Navigate to **This PC > Properties.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/this-pc-properties-install-java-8-cassandra-windows.png)



2. Select **the Advanced system settings** option.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/advanced-system-settings-java-8-cassandra.png)

3. Click **Environment Variables…**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/system-properties-enviormnet-variables-java-cassandra-windows.png)

4. Double-click on the existing **Path** system variable.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/edit-path-variable-python-2.7.png)

5. Select **New** and then **Browse** to locate the Python installation folder quickly. Once you have confirmed that the path is correct, click **OK.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/add-new-python-2.7-variable-path-windows.png)

6. Add the Python 2.7 **path** to the Path system variable by selecting **OK.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/add-python-2.7-variable-path-enviornment.png)

## **Download and Set Up Apache Cassandra**



1. Visit the [official Apache Cassandra Download page](https://www.python.org/downloads/release/python-2718/) and select the version you would prefer to download. Currently, the latest available version is 3.11.6.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/download-latest-cassandra-version-windows.png)

:information_source:  **Note:** It is always recommended to verify downloads originating from mirror sites. The instructions for using GPG or SHA-512 for verification are usually available on the official download page.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/apache-download-mirror-link-windows.png)

4. Unzip the compressed tar.gz folder using a compression tool such as 7-Zip or WinZip. In this example, the compressed folder was unzipped, and the content placed in the **C:Cassandraapache-cassandra-3.11.6** folder.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/content-of-untarred-cassandra-windows-folder.png)

### **Configure Environment Variables for Cassandra**
Set up the environment variables for Cassandra to enable the database to interact with other applications and operate on Windows.

**1. Go to This PC > Properties.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/this-pc-properties-install-java-8-cassandra-windows.png)

2. Go to **Advanced system settings.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/advanced-system-settings-java-8-cassandra.png)

3. Click the **Environment Variables…** button

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/system-properties-enviormnet-variables-java-cassandra-windows.png)

4. Add a completely new entry by selecting the **New** option.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/add-new-system-variable-windows-java-cassandra.png)

5. Type CASSANDRA_HOME for Variable name, then for theVariable value column select the location of the unzipped **Apache Cassandra folder**.

Based on the previous steps, the location is **C:Cassandraapache-cassandra-3.11.6.** Once you have confirmed that the location is correct, click **OK.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/cassandra-add-enviornment-variable-windows.png)

6. Double click on the **Path** variable.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/edit-path-variable-python-2.7.png)
7. Select **New** and then **Browse**. In this instance, you need to add the full path to the bin folder located within the Apache Cassandra folder, **C:Cassandraapache-cassandra-3.11.6bin.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/add-cassandra-bin-folder-path-system-variable.png)

8. Hit the **OK** button and then again **OK** to save the edited variables.

## **Start Cassandra from Windows CMD**

Navigate to the Cassandra bin folder. Start the Windows Command Prompt directly from within the bin folder by typing _cmd_ in the address bar and pressing **Enter.**

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/open-cmd-from-cassandra-bin-folder.png)
Type the following command to start the Cassandra server:
```
cassandra
```

The system proceeds to start the Cassandra Server.

![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/start-cassandra-windows-command-prompt.png)
