# Step 1 - Installing Java
- The first step is to check the availabilty of Java in the system.
>$ java -version

![alt text](javaversion-1.png)

# Step 2 - Installing Hadoop and HDFS
- Next we need to download the hadoop latest version from the following link **[Apache Hadoop Releases page](http://hadoop.apache.org/releases.html)**

![alt text](<Screenshot 2024-02-08 at 5.51.46 PM-1.png>)

- Next we need to download the tar file as shown below

![alt text](<Screenshot 2024-02-08 at 5.58.12 PM-1.png>)

>$ wget https://dlcdn.apache.org/hadoop/common/hadoop-3.3.1/hadoop-3.3.1.tar.gz

![alt text](<Screenshot 2024-02-08 at 6.02.11 PM-1.png>)

- Now we need to extract the tar file using the following command.

>$ tar -xzvf hadoop-3.3.1.tar.gz

- Finally, we move the extracted files into /usr/local, the appropriate place for locally installed software:

>$ sudo mv hadoop-3.3.6 /usr/local/hadoop

- Now open the document containing the environment variable settings

>$ cd /opt/homebrew/Cellar/hadoop/3.3.6/libexec/etc/hadoop

- then open hadoop-env.sh with any editor, I will use vscode

>$code hadoop-env.sh

- We need to find  JAVA_HOME on that file and add our local Java path on on hadoop-env.sh

![alt text](<Screenshot 2024-02-08 at 6.21.14 PM-1.png>)

![alt text](<Screenshot 2024-02-08 at 6.22.08 PM-1.png>)

- Now we need to make changes to the core files. The below command will open the file in VScode

>$ cd /opt/homebrew/Cellar/hadoop/3.3.6/libexec/etc/hadoop 

>$ code core-site.xml
- and add the following configuration to the file. 

![alt text](<Screenshot 2024-02-08 at 6.28.26 PM-1.png>)

- Now we need to make changes to hdfs files. The below command will open the file in VScode
>$ code hdfs-site.xml

![alt text](<Screenshot 2024-02-08 at 6.33.41 PM-1.png>)

- Now we need to make changes to mapred files. The below command will open the file in VScode
>$ code mapred-site.xml

![alt text](<Screenshot 2024-02-08 at 6.36.03 PM-1.png>)

-Now we need to make changes to yarn files. The below command will open the file in VScode
>$ code yarn-site.xml

![alt text](<Screenshot 2024-02-08 at 6.38.18 PM-1.png>)

![alt text](<Screenshot 2024-02-08 at 7.01.55 PM-2.png>)

- Now we need to go to the system preferences and and turn on remote login

![alt text](<Screenshot 2024-02-08 at 6.45.08 PM-1.png>)

# Step 3 - Starting Hadoop

- Now we need to run the following command in the terminal.

>$ hadoop namenode -format

- The hadoop namenode -format command is used to format the Hadoop Distributed File System (HDFS) Namenode.
- The namenode -format command initializes the HDFS Namenode. During this process, it prepares the filesystem metadata and creates the necessary directory structures.
- After running this command, you would usually proceed to start the HDFS daemons, including the Namenode and Datanodes, to make the HDFS cluster operational.

![alt text](<Screenshot 2024-02-08 at 7.01.55 PM-2-1.png>)

- Now run the following command. The start-all.sh script is typically used to start all Hadoop daemons in a Hadoop cluster. This script is part of the Hadoop distribution and is located in the sbin directory of your Hadoop installation. The primary purpose of start-all.sh is to launch the various Hadoop daemons that make up a Hadoop cluster.

>$ ./start-all.sh

- And now we need to type jps to have confirmation that all the parts of Hadoop have been installed and running. You should see something like this.
![alt text](<Screenshot 2024-02-08 at 7.29.35 PM-1.png>)

## Hadoop UI:

![alt text](<Screenshot 2024-02-08 at 7.31.42 PM-1.png>)

- Add SSH security keys. These commands are used for generating SSH key pairs, adding the public key to the authorized keys file, and setting the appropriate permissions on the SSH key files.
>$ ssh-keygen -t rsa -P '' -f ~/.ssh/id_rsa

>$ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys

>$ chmod 0600 ~/.ssh/id_rsa.pub

# Step 4 - Putting Files into HDFS

- We need to create a directry in HDFS and put two text files into it that which we need to run it on wordcount jar file.
