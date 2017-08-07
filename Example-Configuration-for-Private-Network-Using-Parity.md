To run mantis in private network with parity you have to start with:

`mantis -Dconfig.file=path_to_configuration_file.conf`

You have to update configuration_file.conf to set correct bootstrap node addresses and patch to custom genesis file (in the parity configuration you also have to update bootstrap nodes)

To run multiple nodes on single machine you have to set unique ports for each nodes as well as unique `datadir`

Example application configuration file for mantis is (configuration_file.conf)
```
include "application.conf"
include "network.conf"
include "storage.conf"
include "blockchain.conf"
include "sync.conf"
include "misc.conf"

mantis {
  datadir = ${user.home}"/.mantis_prv1"
  network.server-address.port = 9078
  network.discovery.port = 30305
  network.rpc.port = 8548
  sync.do-fast-sync = false

  network {
    discovery.bootstrap-nodes = [
      #put here addresses of other nodes in network
      "enode://f2345158a9e4a6c657ea93cc2eba67cee3d3e178afe5266813fec3ca984385cb44afa6a18a1987c491a9eb227661e8a36d73d773a285c53a9e6a8922b1dcf0c1@192.168.1.207:30303"
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

    chain-id = "33"

    #update this to correct path
    custom-genesis-file = "/path_to/prv.json"
  }
}
```
Example genesis configuration for mantis is (`prv.json`)
```
{
  "difficulty": "0x200",
  "extraData": "0x00",
  "gasLimit": "0x2fefd8",
  "nonce": "0x0000000000000042",
  "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "timestamp": "0x0",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {
    "d7a681378321f472adffb9fdded2712f677e0ba9": {"balance": "1606938044258990275541962092341162602522202993782792835301376"}
  }
}
```

To start mining you need to run a miner, for example `ethminer`
To start mining with ethminer run (`-C` is for cpu only mining) `ethminer -C -F 127.0.0.1:8546`

For parity you can use this custom chain file (`parity_prv.json`):
```
{
  "name": "prv",
  "engine": {
    "Ethash": {
      "params": {
        "gasLimitBoundDivisor": "0x0400",
        "minimumDifficulty": 131072,
        "difficultyBoundDivisor": "0x0800",
        "durationLimit": "0x0d",
        "blockReward": "0x4563918244F40000",
        "registrar": "",
        "homesteadTransition": 494000,
        "eip150Transition": 1783000,
        "eip155Transition": 1915000,
        "eip160Transition": 1915000,
        "ecip1010PauseTransition": 1915000,
        "ecip1010ContinueTransition": 3415000,
        "eip161abcTransition": "0x7fffffffffffffff",
        "eip161dTransition": "0x7fffffffffffffff"
      }
    }
  },
  "params": {
    "accountStartNonce": "0x00",
    "maximumExtraDataSize": "0x20",
    "minGasLimit": "0x1388",
    "networkID": "0xa",
    "chainID": "0x33",
    "eip98Transition": "0x7fffffffffffff"
  },
  "genesis": {
    "seal": {
      "ethereum": {
        "nonce": "0x0000000000000042",
        "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
      }
    },
    "difficulty": "0x200",
    "author": "0x0000000000000000000000000000000000000000",
    "timestamp": "0x00",
    "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x00",
    "gasLimit": "0x2fefd8",
    "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347"
  },
  "nodes": [
   //put here addresses of other nodes in network
"enode://c2328c3e7857106585dbb59b712ac2ab9443d4f0b55b77451fbf33c0dda58b882f0683c4c9222cbf8d1d6893e7f926d487630810202a2c75ec6dd996dbe84715@192.168.0.12:30303"
  ],
  "accounts": {
    "d7a681378321f472adffb9fdded2712f677e0ba9": {
      "balance": "1606938044258990275541962092341162602522202993782792835301376",
      "nonce": "0"
    }
  }
}
```

To start parity with this custom chain use 

`parity --chain /path_to/parity_prv.json`