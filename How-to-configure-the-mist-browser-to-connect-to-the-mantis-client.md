## Prerequisites

### Mist browser

Latest version of Mist wallet should be downloaded from [here](https://github.com/ethereum/mist/releases)

### Run Mantis

Follow [this instructions](index) in order to setup and run the mantis client. 

## Connecting Mist Browser to Mantis

If you are running Mantis in RPC default port `8548` you need to start Ethereum wallet as:

**Windows**
- Open cmd.exe
- Mist.exe --rpc `http://localhost:8546`

**Linux**
- Open your terminal of choice
- Run `ethereumwallet --rpc http://localhost:8546`

**Mac**
- Open Terminal.app
- Run `ethereumwallet --rpc http://localhost:8546`

## Caveats
- As Mist is no longer maintained for ETC chain, this guide was created using ETH branch. There might be some cases when deploying a contract, compiled code will fail to run because some incompatibilities between forks. If that's your case, some workarounds are:
  - Grab the ETC mist version from [here](https://github.com/ethereumproject/mist/releases) (there is no pre-built version for linux)
  - Deploy your contract using [Web3.js](https://github.com/ethereum/wiki/wiki/JavaScript-API#web3ethcontract)
- Some Mist issues were detected while doing regression testing. Refer to this [link](Mist-Integration-Testing-Report) to see the complete list
