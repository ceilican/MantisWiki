# Setup environment
geth v3.3.0-1-gdd95f05

# Geth command and genesis
`geth-classic --cache=1024 --maxpeers 1 --rpccorsdomain "*" --rpc --rpcapi eth,web3,personal,admin,net --datadir $PWD/datadir --rpcport 8545 --port 30309 --nodiscover --identity "TestnetMainNode" --networkid 1999 console`

Geth genesis json:
```
{
    "config": {
        "chainId": 15,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
    "difficulty": "200",
    "gasLimit": "2100000",
    "alloc": {
        "7df9a875a174b3bc565e6424a0050ebc1b2d1d82": { "balance": "300000" },
        "f41c74c9ae680c1aa78f42e5647a62f353b7bdde": { "balance": "400000" }
    }
}
```

# Mantis
Custom genesis json:
```
{
  "difficulty": "0x00000000C8",
  "extraData": "0x",
  "gasLimit": "0x200B20",
  "nonce": "0x0000000000000000",
  "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "timestamp": "0x0",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {
    "7df9a875a174b3bc565e6424a0050ebc1b2d1d82": { "balance": "300000" },
    "f41c74c9ae680c1aa78f42e5647a62f353b7bdde": { "balance": "400000" }
  }
}
```
  
Config changes:
```
mantis.network.peer.network-id = 1999
mantis.blockchain.chain-id = "15"
mantis.blockchain.custom-genesis-file = "path/to/custom genesis json"
mantis.sync.min-peers-to-choose-target-block = 1
mantis.network.bootstrap-nodes = ["enode://from-geth-console"]
```

# Running Ethminer with Mantis client
`./ethminer/ethminer -C -F 127.0.0.1:8546`

# Result
Transactions are properly mined and broadcasted to geth.