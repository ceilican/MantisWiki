## Stop syncing, start testing!

Even `Fast Sync` - downloading a state trie snapshot from the peer network can take considerable time, anywhere from about seven hours to a few days depending on the network state, the quality of the network connection and the hardware used to store the data. 

In order to shorten the time needed to get a mantis client up to date with the most recent bloc in the network we provide a bootstrap zip file containing a mantis database pre loaded with a recent version of the chain. Unzip this to the datadir  folder (`$HOME/.mantis` by default) check the md5sum checksum and then start up the client. The client will begin to process transactions and blocks at the point the database snapshot was taken reducing the time needed to sync to the most recent block to minutes rather than hours ... 

[mantis-cli-beta1-bootstrap-db](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/mantis-cli-beta1-bootstrap-db.zip)

[mantis-cli-beta1-bootstrap-morden-db](https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/mantis-cli-beta1-bootstrap-morden-db.zip)

