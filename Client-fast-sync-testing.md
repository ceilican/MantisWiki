* I started fast sync on EC2 on 14:10 CEST 26th of July with target block `4163902`
* On 16:05 it is on 733184 block, no dead loop, no stuck
* Around block 1389840 10:00 CEST 27th of July we blacklisted all peers and we are receiving lot of transactions not targeted at etereum classic chain
* 10:05 CEST we unbloacklisted 1 peer and we are syncing again (Block: 1392592/4163902)
* 11:32 CEST restart with new configuration lowering the blacklist duration (Block: 1434256/4163902)
* 12:16 CEST restart with latest version of application (Block: 1488656/4163902)
* 12:25 CEST restart with removed trace from message decoder error (Block: 1491216/4163902)
* 12:29 CEST restart with pruning set to `archive` because fast sync was started without pruning
* 12:51 CEST restart update update `nodes-per-request` 1000 -> 500 (Block: 1507984/4163902)
* 13:35 CEST peers are responding with `11:35:07.329 i.i.e.b.s.SyncBlockHeadersRequestHandler - Received 0 block headers in 1556 ms` (Block: 1512464/4163902)
* 13:37 CEST restart to get better peers, updated `connect-max-retries` 1 -> 5
* 15:03 CEST restart with configuration changes from https://github.com/input-output-hk/etc-client/pull/261/commits/363742a9d358a2c631af61bc40d428258116c1f8 (Block: 1518416/4163902)
* 16:39 CEST restart with update `nodes-per-request` 500 -> 200 (Block: 1547472/4163902)
* 17:04 CEST restart with update block-headers-per-request 2048 -> 200 (Block: 1555600/4163902)
* 10:55 CEST 28th of July restart with changes from https://github.com/input-output-hk/etc-client/pull/261/commits/b0761e8fa8e50df25e276d67b53b7ea2f16e7474 (Block: 1736792/4163902)



-----------------------------------------------------------------------------------------------

* 11:05 CEST restart from empty data dir because blacklisting all peers with message `got empty mpt node response for known hashes`, target MPT was probably already pruned from peers, target block is `4175269`
* 13:51 CEST Block: 776848/4175269 State: 3228429/3234860 nodes
* 16:37 CEST restart with https://github.com/input-output-hk/etc-client/pull/264 branch (prioritize nodes download because they can be pruned) Block: 1005144/4175269 State: 3238067/3246877 nodes
* 17:03 CEST Block: 1042776/4175269 State: 4665247/4671393 nodes
* 17:14 CEST we got stuck on timeouts on all fast sync elements but timeouts stopped at 17:29 CEST we suspect that network was under load
* 17:33 CEST Block: 1056216/4175269 State: 4902847/4906683 nodes
* 17:46 CEST Block: 1074456/4175269 State: 5170859/5174391 nodes
* 11:13 CEST 31st of July Block: 3245472/4175269 State: 21775445/21775445 nodes syncing from 1 peer
* 19:59 CEST Block: 3628064/4175269. State: 21775445/21775445 nodes. Stack with 0 peers: Peers waiting_for_response/connected: 0/0 (0 blacklisted)
* 09:54 CEST restart it was not able to connect to any new peer
* 15:43 CEST finished fast sync and switched to regular sync it is now on 4176799th block

--------------------------------------------------------------------------------------------------------

* 14:20 CEST 31st of July started second EC2 instance with fast sync with disabled discovery, target block is `4194826`
* 18:06 CEST Block: 430008/4194826. State: 4216017/4223787 nodes.
* 19:53 CEST Block: 432632/4194826. State: 4246017/4253101 nodes. 
* 09:54 CEST 1st of August Block: 731896/4194826. State: 12391323/12406325 nodes, connected to 6 peers
* 15:58 CEST Block: 736696/4194826. State: 14047204/14057012 nodes. Connected to 6 peers
* 10:15 CEST 2nd of August Block: 841464/4194826. State: 18938830/18951608 nodes. Connected to 6 peers
* 14:16 CEST Block: 841464/4194826. State: 20012279/20019682 nodes. Connected to 6 peers
* 11:48 CEST 3rd of August Block: 1790520/4194826. State: 21781789/21781789 nodes. Connected to 6 peers
* 12:13 CEST Block: 1797200/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 2/6 (4 blacklisted) we started blacklisting peers because of timeouts on block bodies and receipts
* 12:21 CEST Block: 1797728/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 5/5 (0 blacklisted). no more blacklisting
* 07:07 CEST 4th of August Block: 2773696/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 5/6 (1 blacklisted). 
* 13:34 CEST Block: 2776216/4194826 State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 5/6 (1 blacklisted).
* 16:35 CEST Block: 3004252/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 5/6 (1 blacklisted).
* 10:45 CEST 7th of August Block: 3004252/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 1/6 (0 blacklisted). Asking for block headers but getting empty responses from peer `Received 0 block headers in 268 ms`, restarted, now it is syncing again
* 16:46 CEST Block: 3004252/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 5/6 (1 blacklisted). 
* 17:23 CEST sync was stuck on 3004252 it was showing only that it is downloading block bodies and receipts but was not asking for block headers, after restart I noticed that it is also asking for block headers but best block is not changing, **Restarted with discovery enabled**
* 19:40 CEST Block: 3029148/4194826. State: 21781789/21781789 nodes. sync was stuck in `Received 0 block headers in 256 ms` loop which we found previously, restarting
* 9:52 CEST 8th of August Block: 3029148/4194826. State: 21781789/21781789 nodes. Getting empty block headers responses, restarted, updated `connect-max-retries` from 2 to 20
* 9:57 CEST it is syncing again Block: 3029332/4194826. State: 21781789/21781789 nodes. Peers waiting_for_response/connected: 3/3 (0 blacklisted).
* 10:29 CEST 9th of August it is in loop asking for block headers from peer that is responding with 0 block headers, Block: 3322756/4194826. State: 21781789/21781789 nodes. 
* 10:41 CEST **restarted with** `fix/randomPeerSelection` branch which addresses issue of sticking with one peer when asking for block headers, client is syncing again
* 11:32 CEST Block: 3492412/4194826. State: 21781789/21781789 nodes. No dead loop, connected to 6 peers