The mantis client is highly flexible and it's behavior at runtime can be controlled through its configuration files. 

All mantis configuration files live in the `conf` folder under the application root folder.

```
application.ini
blockchain.conf
logback.xml
mantis.conf
misc.conf  
morden.conf  
morden.json  
network.conf
storage.conf  
sync.conf
```
### application.ini
This is the entry point for the application configuration, it points the application at the `mantis.conf` file, and passes a stack size to the JVM. This is required to allow the EVM a sufficient stack size.
```
-Dconfig.file=./conf/mantis.conf -Dlogback.configurationFile=./conf/logback.xml -J-Xss10M
```
More JVM parameters can be added here. 

Note that this ini file is only relevant on linux and MacOS, on Windows the `mantis_config.txt` is picked up and serves the same role.

### mantis.conf
The mantis conf file is the umbrella file from where all other configuration files are included. 
Note that to make life easier the configuration for the `morden` testnet is pre configured and to enable it the `include morden.conf` line must be un commented.

```
# This is the main configuration file for the Mantis ETC client.
# It consist of series of includes where actual settings are defined.


# This where all the default settings are defined (this file is packaged within the executable).
# It should always go at the top.
include "application.conf"

# The following include are where users are expected to defined their own configuration overrides.
# To override a setting, go to a specific file, uncomment a setting and provide a value.
include "network.conf"
include "storage.conf"
include "blockchain.conf"
include "sync.conf"
include "misc.conf"

# Uncomment the following include to connect to the testnet Morden.
# Note that any settings in this file will override the ones defined in the files above
# include "morden.conf"
```
`network`, `storage`, `blockchain`, `misc` and `sync` are logically grouped configuration parameters to make working with the configuration easier for the user. 

### logback.xml
This file controls the level of logging to both the console and file. By default a useful level of logging is directed to the console and slightly more verbose logging is logged to file. The file is named `mantis.log`. The policy for preventing the file from growing too large is controlled by `rollingPolicy` in this file. By default an archive of ten zip files of logs is maintained. More info on logback.xml [here](https://logback.qos.ch/manual/configuration.html)

### Common Configuration Options
This section details how to change some of the more common configuration options.

#### Morden
By default the client is configured to connect and download the `classic` chain. To change this to the `morden` test chain un-comment the line 

`# include "morden.conf"`

in the `mantis.conf` file such that it reads 

`include "morden.conf"`

#### Data Folder
By default the blockchain and all other files that mantis creates are stored in the users home folder under a sub folder called `.mantis`. This setting is found in the `storage.conf` file.

`# datadir = ${user.home}"/.mantis"`

In order to change this setting un comment this line and replace the value. For example to change the datadir to `/data/my_mantis` replace the above line with the following ...

`datadir = "/data/my_mantis"`

#### Discovery
By default the discovery functionality is active. The network is queried for more potential nodes using a partial implementation of the kadelmia discovery protocol. To prevent this and use *only* the bootstrap nodes as listed in the `network.conf` there is a line. 

`# discovery-enabled = true`

This commented out line shows the default value for the discovery protocol (true). To disable `discovery` un comment it and change the value to `false`.

`discovery-enabled = false`

#### Fast Sync
By default fast sync is enabled, to disable this edit the `sync.conf` and locate the following line 

`# do-fast-sync = true`

Un comment the line and replace 'true' with 'false'

`do-fast-sync = false`

#### Pruning
By default the database is pruned of state trie nodes no longer needed, to prevent this functionality and keep all intermediate state nodes edit the `storage.conf` file and replace 

`# mode = "basic"`

with 

`mode = "archive"`

