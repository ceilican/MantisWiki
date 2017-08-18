Currently our client supports mining only with external miner connected through RPC (like ETH miner)

We have to generate 3 values for miner to work (they are prepared here https://github.com/input-output-hk/mantis/blob/master/src/main/scala/io/iohk/ethereum/jsonrpc/EthService.scala#L441)

Target - target difficulty of mined block, that is encoded as byte array

Seed - it is epoch seed that is derived from block number (yellow paper contains incorrect description of derivation seed for epoch 0 is not kec256(32 zero bytes) but 32 zero bytes there is open issue for that https://github.com/ethereum/yellowpaper/issues/312)

PowHeaderHash - hash to calculate PoW, it is kec256(rlp_encoded(block_header)), but block_header is without nonce and PoW as they will be calculated while mining, before obtaining PowHeaderHash we have to execute transactions to get new mpt state root (which is done here https://github.com/input-output-hk/mantis/blob/master/src/main/scala/io/iohk/ethereum/mining/BlockGenerator.scala#L31)

It is important to know that Mantis has no control over external miner, it is up to external miner to request and submit work through RPC with `eth_getWork` and `eth_submitWork`