## Using the Bootstrap Databases 

### Classic Bootstrap
Even `Fast Sync` - the process of downloading a state trie snapshot from the peer network - can take considerable time, anywhere from about seven hours to a few days depending on the network state, the quality of the network connection and the hardware used to store the data. 

In order to shorten the time needed to get a mantis client up to date with the most recent block in the network we provide a bootstrap zip file containing a mantis database pre loaded with a recent version of the chain. 

Download the [mantis-cli-beta1-bootstrap-db](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/mantis-cli-beta1-bootstrap-db.zip) classic bootstrap database and generate a checksum for this file using 

`md5sum mantis-cli-beta1-bootstrap-db.zip`

OR on Windows

`CertUtil -hashfile mantis-cli-beta1-bootstrap-db.zip MD5` 

OR on MacOS

`md5 mantis-cli-beta1-bootstrap-db.zip`

The result should read 

`3a7bceeb1816de2e481d6a280c73e4e1 mantis-cli-beta1-bootstrap-db.zip`

On Linux and MacOS unzip this to the datadir folder. Assuming the default `$HOME/.mantis` ...
```
cd ~/.mantis
unzip ~/mantis-cli-beta1-bootstrap-db.zip
```
On Windows extract the files by right clicking on the zip file and using `Extract All...`

This should create a folder `~/.mantis/leveldb` containing the database snapshot files.

Start the client (using `bin/mantis` or `bin\mantis.bat` on Windows) and the client will begin to process transactions and blocks at the point the database snapshot was taken reducing the time needed to sync to the most recent block to an hour rather than eight hours ... 

### Morden Bootstrap

Download the [mantis-cli-beta1-bootstrap-morden-db](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/mantis-cli-beta1-bootstrap-morden-db.zip) and generate a checksum for this file using 

`md5sum mantis-cli-beta1-bootstrap-morden-db.zip`

OR on Windows

`CertUtil -hashfile mantis-cli-beta1-bootstrap-morden-db.zip MD5` 

OR on MacOS

`md5 -hashfile mantis-cli-beta1-bootstrap-morden-db.zip` 


The result should read 

```
d90949754c0990b1ce72aab2decf0bea  mantis-cli-beta1-bootstrap-morden-db.zip
```

On Linux and MacOS Unzip this to the datadir folder. Assuming the default `$HOME/.mantis` ...
```
cd ~/.mantis
unzip ~/mantis-cli-beta1-bootstrap-morden-db.zip
```

On Windows extract the files by right clicking on the zip file and using `Extract All...`

This should create a folder `~/.mantis/leveldb` containing the database snapshot files.

Un comment the reference to `morden.conf` in the `mantis.conf` configuration in order to enable morden settings.

Start the client (using `bin/mantis` or `bin\mantis.bat` on Windows) and the client will begin to process transactions and blocks at the point the database snapshot was taken reducing the time needed to sync to the most recent block to minutes rather than hours ... 

