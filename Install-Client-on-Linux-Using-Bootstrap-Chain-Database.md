## Prerequisites

### A Java Virtual Machine with version 1.8.x.

So for example on an EC2 small instance 
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

### The Bootstrap Database
A bootstrap database has been created to support the client.
 
This file is available for download from S3. 

[Chain folder gzip](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/grothendieck-bootstrap-jul27-db.zip)

Or from a command line use ... 

```wget https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/grothendieck-bootstrap-jul27-db.zip```

## Checksum the file 

When the file is fully downloaded (on linux) run the following command 

```md5sum grothendieck-bootstrap-jul27-db.zip```

This should result in a line identical to the following ...

```cfe28f39d0ce1e46c7cd1f7adc0ab998  grothendieck-bootstrap-jul27-db.zip```

Compare the results of the line on your terminal to the above line, the checksum should be identical.

The default folder for data is `~/.grothendieck`. In order to use the downloaded database create this folder and `cd` into it. Then unzip the file using...

`unzip <path to zip file>/grothendieck-bootstrap-jul27-db.zip`

