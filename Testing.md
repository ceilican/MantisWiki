## Setup

For tests we set up 10 EC2 instances on a private network, we used genesis as bellow:
```
{
  "difficulty": "0x400",
  "extraData": "0x00",
  "gasLimit": "0x2fefd8",
  "nonce": "0x0000000000000042",
  "ommersHash": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
  "timestamp": "0x00",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "alloc": {
    "d7a681378321f472adffb9fdded2712f677e0ba9": {"balance": "1606938044258990275541962092341162602522202993782792835301376"}
  }
}
```
for mining we used ethminer from `https://github.com/Genoil/cpp-ethereum.git` from branch `108` which supports CPU mining

we were testing on ubuntu 16.04, to compile ethminer you need to instal some packages:
```
sudo apt-get -y install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install git cmake libcryptopp-dev libleveldb-dev libjsoncpp-dev libboost-all-dev libgmp-dev libreadline-dev libcurl4-gnutls-dev ocl-icd-libopencl1 opencl-headers mesa-common-dev libmicrohttpd-dev build-essential -y
sudo apt-get install libjsonrpccpp-dev -y
```

## Testing
Firstly we run nodes not connected to each other, this way nodes got their own versions of blockchain after chains were ~60 blocks long we connected them together and let them mine and resolve conflicting branches at the same time.

We let them run for 3 days and after checking did not notice any error in logs, nodes are roughly on the same block and they are mining without any issue