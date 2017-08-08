It seems that sending a transaction with a gas limit exceeding block gas limit (currently 4704624) results in the transaction not being mined, even though the actual execution costs less gas than the limit. 

With such an "invalid" transactions in the network (and in pending tx pool) it's hard to get any other transaction through. Sending subsequent transactions using rpc sendTransaction method results in assigning a nonce that is one bigger than then previous (pending) transaction. 

Since the previous transaction will not be mined, the one with higher nonce also won't be mined. 

The solution to that is to replace the first transaction with another tx with the same nonce that can be mined.

Additional links:
https://blog.parity.io/announcing-parity-1-7/