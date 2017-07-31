## Set up 

Using an EC2 small instance with 60G of general purpose SSD. 

`java -version` reports 

```
java version "1.8.0_131" 
Java(TM) SE Runtime Environment (build 1.8.0_131-b11) Java HotSpot(TM) 64-Bit Server VM (build 25.131-b11, mixed mode)
```
Client built on Monday 31 July using branch `beta1` and command `sbt dist`

Bootstrap database downloaded from [S3](https://github.com/input-output-hk/etc-client/wiki/Install-Client-on-Linux-Using-Bootstrap-Chain-Database) using 

`wget https://s3.eu-central-1.amazonaws.com/iohk.etc-client.snapshots/grothendieck-bootstrap-jul27-db.zip`

File unzipped to `~/.grothendieck` folder. 

Client unzipped to `~/etc-client-dist` folder.

Client executed in tmux session from `etc-client-0.1` folder using `./bin/etc-client`.

No changes made to configuration.

## Syncing 
Sync began at 11.27 UTC on Block 4170219 (picked up from bootstrap database)

```
11:27:08 Starting block synchronization
11:27:08 Block: 4170219. Peers: 0 (0 blacklisted)
```

12.13 - synchronization progressing as expected ...  
```
12:13:20 Block: 4174651. Peers: 7 (0 blacklisted)
12:13:21 Received 64 block bodies in 926 ms
```
```
13:07:08 Block: 4180883. Peers: 7 (0 blacklisted)
```