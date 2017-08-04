## Testing environment (Small EC2 instance)
```
Hardware: Lenovo ideapad 310

CPU: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz, 2592 Mhz

Mem: 8GB

Disk: 300GB 

OS: Windows 10

openjdk version "1.8.0_144_b01"
```

## Version
```
commit 419c2835b26eed9b4309e473cfd5f0e99e4ba12e
Merge: bbd3d508 9fd2e89e
Author: Nicolas Tallar <nicolas.tallar@iohk.io>
Date:   Thu Aug 3 17:32:03 2017 -0300

    Merge branch 'phase/beta1' of github.com:input-output-hk/etc-client into fix/keysFileNameWindows

```

## Scenarios tested with results

### Syncing (Fast Sync)

Synced for ~4-5 hours without any problems, last status:
```
11:54:19 Block: 924240/4213768. Peers waiting_for_response/connected: 3/3 (0 blacklisted). State: 12890960/12897149 nodes.
```

### Private chain with mining

#### Setup

* Miner: Genoil's Ethereum AMD+NVIDIA GPU Miner v1.1.7 (Windows) - Used via OpenCL.
* Mantis client:
   * Setup private chain on Mantis client.
   * Imported account for use as coinbase.

#### Result

Several blocks were mined, which were included in the blockchain and were reported in Mist.