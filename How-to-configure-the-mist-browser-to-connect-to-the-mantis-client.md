## Prerequisites

### Mist Browser or Ethereum Wallet

1. Download and install the latest version of [the Mist browser or the Ethereum Wallet](https://github.com/ethereum/mist/releases). (Before choosing which one to download, you may want to learn the [difference between Mist and the Ethereum Wallet](https://ethereum.stackexchange.com/questions/2690/what-is-the-relationship-between-mist-and-ethereum-wallet).)


### Mantis

1. Download, install and setup the [Mantis client](Home). 

2. Enable the "personal" JSON-RPC API over the HTTP endpoint in the `./conf/Network.conf` file, by ensuring that the file contains the following line in the `rpc` section:
   ```
   apis = "eth,web3,net,personal" 
   ```

3. Run the mantis client.

## Connecting the Mist Browser or the Ethereum Wallet to Mantis

If you are running Mantis with the default RPC port `8546`, you need to start the Mist Browser or the Ethereum Wallet with `--rpc http://localhost:8546` as a command line parameter, as shown below:

**Windows**
1. Open cmd.exe
2. Run `Mist.exe --rpc http://localhost:8546`

**Linux**
1. Open your terminal of choice
2. Run `ethereumwallet --rpc http://localhost:8546`

**Mac**
1. Open Terminal.app
2. Run `ethereumwallet --rpc http://localhost:8546`

## Caveats
As Mist is no longer maintained for the ETC chain, this guide was created using the ETH branch. There might be some cases when the compiled code of a deployed contract will fail to run because of incompatibilities between forks. If that happens, some workarounds are:
  - Download and use the pre-built [ETC Mist version](https://github.com/ethereumproject/mist/releases). (Note: there is no pre-built version for Linux.)
  - Deploy your contract using [Web3.js](https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethcontract).

Some Mist issues were detected while doing regression testing. Refer to the [Mist Integration Testing Report](Mist-Integration-Testing-Report) for a complete list.


