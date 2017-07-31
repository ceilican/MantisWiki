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

