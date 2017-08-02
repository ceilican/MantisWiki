# RUN 1
### Hardware - Small EC2 instance 

2G RAM, 60G HD (general purpose SSD)

Run from dist created from branch "beta1" (plus outstanding PRs) on Tuesday Aug 1 11:22:44 IST 2017

```
08:09:04 Block: 1000216/4200094. Peers waiting_for_response/connected: 1/6 (1 blacklisted). State: 18813017/18815028 nodes
```
```
11:22:04 Block: 1020600/4200094. Peers waiting_for_response/connected: 3/7 (0 blacklisted). State: 20619238/20621259 nodes.
```
# RUN 2

EC2 Large Instance (network moderate)
Started - Wed Aug  2 11:19:30 UTC 2017

```
11:21:43 Block: 28328/4206059. Peers waiting_for_response/connected: 8/8 (0 blacklisted). State: 149027/158735 nodes.
```
```
11:56:13 Block: 274360/4206059. Peers waiting_for_response/connected: 7/7 (0 blacklisted). State: 2372650/2379673 nodes
```
```
13:10:13 Block: 713144/4206059. Peers waiting_for_response/connected: 6/6 (1 blacklisted). State: 6881071/6896739 nodes
```
```
16:14:43 Block: 769912/4206059. Peers waiting_for_response/connected: 5/5 (0 blacklisted). State: 19482675/19490954 nodes
```
State trie downloaded .... .9 of 4.2 million blocks to go...
```
17:26:13 Block: 916504/4206059. Peers waiting_for_response/connected: 4/4 (0 blacklisted). State: 21785288/21785288 nodes
```
# RUN 3

Windows 10 Home Edition (Version 1607)

### Editing Config Files on Windows
The config file are created for Linux, in order to make the files readable on windows use
```
type misc.conf | more /P > out.conf
```
And then rename the `out.conf` to the original file name. Apologies, this will be remedied in later versions.

Intel i7 4GHz CPU

32G RAM
Standard large disk (!?)

First, JRE needed to be installed used latest release v 1.8 147
Then windows does not support paths in `application.ini` or `NativePRNG` had to fix that. 

Run began successfully at 14.50 pm Wednesday 2nd August.
(Stopped 3 times to check launch error fix on Windows. )