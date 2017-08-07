## Testing environment
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

Synced for ~15-16 hours without any problems, last status:
```
20:59:50 Block: 1355352/4213768. Peers waiting_for_response/connected: 4/4 (0 blacklisted). State: 18054264/18068629 nodes.
```
Size of the database: 5.83GB.

### Private chain with mining

#### Setup

* Miner: Genoil's Ethereum AMD+NVIDIA GPU Miner v1.1.7 (Windows) - Used via OpenCL.
* Mantis client:
   * Setup private chain on Mantis client, with only the Mantis client.
   * Imported account for use as coinbase.

#### Result

Several blocks were mined (with and without transactions), which were included in the blockchain and were reported in Mist.