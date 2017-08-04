# Goal

Check parity sync from our client

# Testing environment

Hardware: Amazon EC2-Instance

Mem: 2GB

OS: Ubuntu 16.04.2, kernel 4.4.0-1022-aws

JVM: oracle java version "1.8.0_131"

Parity: version Parity/v1.6.10-stable-1a5b176-20170721/x86_64-linux-gnu/rustc1.18.0

# Mantis config

We started a seed node based on a prebuilt etc chain bootstrap database running up to date with latest network block

# Parity configuration
```
parity --chain classic --jsonrpc-interface 127.0.0.1 --jsonrpc-port 8545 --author 00F538Bb0d2dc3F6DEd39Fc0279099D8cD43F956 --geth --base-path ~/parity_data --logging trace --jsonrpc-apis parity_accounts,web3,eth,net,parity,traces,rpc,parity_set,personal --mode active --no-discovery --bootnodes enode://0eebcc4c199363402dbe2c32257c2a3bb7754ab49b8fefd931f30fcd909b6011eba4801deea5f1260ed3c0a1cac56b0f0778c4723631ac846c4e54882d816a45@52.214.185.231:9076 --network-id  1
```

# Version
```
commit 6a09b0d3567981fe244cd59d41792f30515f4240
Author: Radek Tkaczyk <radek.tkaczyk@iohk.io>
Date:   Wed Jun 28 16:24:41 2017 +0200

    unify test timeouts: updated a few missed 
```

# Test Log

- 28/07
  - time: 11:02
  - status: connected to our fast sync node
- 29/07
  - time: 9:22
  - status: best block number 94656
- 31/07
  - time: 9:27
  - status: best block number 94656
  - notes: it seems parity got stucked while syncing

# Result

After doing some analysis we found that parity got stucked because our seed node was missing block body #94657. This issue was fixed in https://github.com/input-output-hk/etc-client/pull/268