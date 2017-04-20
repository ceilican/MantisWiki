_The purpose of this page is to keep track of all the blocks that failed to execute while we were working on TX execution. This is just a history of problems and fixes. It should help us deal with possible regressions and provide more insight into interpretations of YP._

#### 62102
In progress???

#### 53145
Logs were not discarded in the event of VM error

#### 50111
Gas refunds were not included in block's cumulative gas. This may be a bug in YP, see: https://github.com/ethereum/yellowpaper/issues/299

#### 49157
????

#### 49018
Code deposit gas not handled correctly for contract creating TX

#### 48462
Incorrect handling of value transfer from A to A (same sender and recipient)

#### 47205
Nonce increased twice for contract creating TX

#### 46000
State not rolled back after OOG error