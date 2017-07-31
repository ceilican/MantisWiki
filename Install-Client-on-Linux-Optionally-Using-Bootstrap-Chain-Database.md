## Prerequisites

### A Java Virtual Machine with version 1.8.x.

A Java Virtual Machine (JVM) is required to run the client. The version must be 1.8.x. The client has not been tested with JVM 1.9.

To check the JVM version use `java -version`. For example on a recently created  EC2 small instance the response is ...
```
java version "1.8.0_131"
Java(TM) SE Runtime Environment (build 1.8.0_131-b11)
Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)
```
### Disk Space 
The database for the Ethereum Classic chain take approximately 15G of disk space. 
Appropriate overhead will be needed for the chain to grow into the future. 
An SSD of at least 25G is recommended.  

### Memory (RAM) 
The client has been tested extensively on EC small instances with 2G of RAM. 
This is sufficient to run the client and the miner (however it is not sufficient to *build* the miner)

## Downloads
### The Client Binary
This client is distributed as a `zip` archive and can be downloaded from the [releases](https://github.com/input-output-hk/etc-client/releases) section of the github repository. 
 
### The Bootstrap Database (Optional)
A bootstrap database has been created to support the client.
 
This file is available for download from S3. 

[Bootstrap zip](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/grothendieck-bootstrap-jul27-db.zip)

Or from a command line use ... 

```wget https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/grothendieck-bootstrap-jul27-db.zip```

### Checksum the Bootstrap Database Archive 

When the file is fully downloaded (on linux) run the following command 

```md5sum grothendieck-bootstrap-jul27-db.zip```

This should result in a line identical to the following ...

```cfe28f39d0ce1e46c7cd1f7adc0ab998  grothendieck-bootstrap-jul27-db.zip```

Compare the results of the line on your terminal to the above line, the checksum should be identical.

The default folder for data is `~/.grothendieck`. In order to use the downloaded database create this folder and `cd` into it. Then unzip the file using...

`unzip <path to zip file>/grothendieck-bootstrap-jul27-db.zip`

## Install the Client

unzip the client archive file downloaded from the previous section. This will create a folder structure as follows -

``` 
etc-client0.1
│   
└───bin
│   
└───conf
│   
└───lib
```
The `lib` folder contains all the jars required to run the client, the `conf` folder contains the configuration files needed to alter the user settings of the client and the `bin` folder contains the scripts to start the client.

### Run the Client

From the `etc-client-0.1` folder use 

`./bin/etc-client`

This command will run the client in the foreground with settings as dictated in the `conf` folder files. 

Note that for long running processes on remote machines it is recommended to use [tmux](https://www.rosehosting.com/blog/getting-started-with-tmux/) or equivalent in order to prevent the client stopping when the terminal is shut down.

## Changing the Default Settings
Following the instructions outlined above including using the bootstrap database should result in a startup similar to the following 
![](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/Start_with_bootstrap.png)

The first block should be around 4.1 million as this is where the snapshot was taken. If you have not used the snapshot 
The default datadir is `~/.grothendieck`. To change this edit the `storage.conf` file in the `conf` folder.

![](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/default_data_dir.png)

Un-comment the `datadir` configuration and replace the value with the preferred value.

```datadir = ${user.home}"/.grothendieck" ```