To run mantis with private network you have to
mantis -Dconfig.file=path_to_configuration_file.conf

example genesis configuration for mantis is (`prv.json`)
```
{
  "difficulty": "0x200",
  "extraData": "0x",
  "gasLimit": "0x2fefd8",
  "nonce": "0x00006d6f7264656e",
  "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "timestamp": "0x0",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "mixHash": "0x00000000000000000000000000000000000000647572616c65787365646c6578",
  "alloc": {
    "0000000000000000000000000000000000000001": { "balance": "1" },
    "0000000000000000000000000000000000000002": { "balance": "1" },
    "0000000000000000000000000000000000000003": { "balance": "1" },
    "0000000000000000000000000000000000000004": { "balance": "1" }
  }
}
```

example application configuration file for mantis is (configuration_file.conf)
```
include "application.conf"
include "network.conf"
include "storage.conf"
include "blockchain.conf"
include "sync.conf"
include "misc.conf"

mantis {
  datadir = ${user.home}"/.mantis_prv"

  #if running more nodes on same machine change ports
  network.server-address.port = 9076
  network.discovery.port = 30303
  network.rpc.port = 8546

  sync.do-fast-sync = false

  network {
    discovery.bootstrap-nodes = [
      #put here addresses of other nodes in network
"enode://d207a638fcb2880b79b051cab39db53223f9103da52d5b086869284e42ca09ef7da7ff372edd25a1c83a8fd5946af4b973b3df45ba4e285c54a1aace339c7990@127.0.0.1:9077"
    ]

    peer.network-id = 10
  }

  blockchain {
    frontier-block-number = "0"
    homestead-block-number = "494000"
    eip150-block-number = "1783000"
    eip155-block-number = "1915000"
    eip160-block-number = "1915000"
    difficulty-bomb-pause-block-number = "1915000"
    difficulty-bomb-continue-block-number = "3415000"

    dao-fork-block-number = "9999999999"
    dao-fork-block-hash = "f376243aeff1f256d970714c3de9fd78fa4e63cf63e32a51fe1169e375d98145"

    account-start-nonce = "1048576"

    chain-id = "33"

    #update this to correct path
    custom-genesis-file = "/path_to/prv.json"
  }
}
```

to start mining you need external miner, for example `ethminer`
to start mining with ethminer run (`-C` is for cpu only mining) `ethminer -C -F 127.0.0.1:8546`