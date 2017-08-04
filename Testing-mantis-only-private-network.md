# Goal

Check if two mantis instances can connect to each other, share blocks and reach consensus in a private chain

# Testing environment

Hardware: Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz

Mem: 12GB

OS: Ubuntu 16.04.2, 4.4.0-83-generic

JVM: openjdk version "1.8.0_131"

# Mantis config

default-genesis.json

```
{
  "difficulty": "0x0000040000",
  "extraData": "0x11bbe8db4e347b4e8c937c1c8370e4b5ed33adb3db69cbdb7a38e1e50b1b82fa",
  "gasLimit": "0x1388000",
  "nonce": "0x0000000000000042",
  "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "timestamp": "0x0",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {}
}
```

client 1 - network.conf

```
mantis {

  network {

    server-address {
      # Listening interface for Ethereum protocol connections
      # interface = "127.0.0.1"

      # Listening port for Ethereum protocol connections
      port = 9075
    }

    discovery {
      # Turn discovery of/off
      discovery-enabled = false

      # Set of initial nodes
      bootstrap-nodes = []
    }

    peer {
      network-id = 3333
    }

    rpc {
      port = 8545
    }
  }
}

```

client 2 - network.conf

```
mantis {

  network {
    discovery {
      # Turn discovery of/off
      discovery-enabled = false

      # Set of initial nodes
      bootstrap-nodes = [
        "enode://5097eeaa0e10e12629755cfba54957989bfad96e8d3d1707379746e168f17eda39c46dd6deff8cbf83848f2748751cd2bdebe844ae4b40428c0ac90b7163e6e1@127.0.0.1:9075"
      ]
    }

    peer {
      network-id = 3333
    }
  }
}
```

# Version
```
commit 24acf16a08fe3be52899ef9e037f807ee88e3f16
Author: Adam Smolarek <adam.smolarek@iohk.io>
Date:   Fri Aug 4 13:41:22 2017 +0200

    add todo for further modifications
```

# Test cases

1. Startup the two nodes and start mining in client1. Blocks should be broadcasted to client2 :white_check_mark: 
2. Shutdown miner in client1 and start it up in client2. Blocks should be broadcasted to client1 :white_check_mark: 
3. Startup miner in client1. Blocks from both clients should be present in resulting blockchain :white_check_mark: 

# Result

Everything ran as expected