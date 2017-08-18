Ethereum uses ECC for transactions digital signature.

EC digital signature contains 2 elements called s and r (x coordinate of ephemeral public key) they are 2 integers, using those 2 values with ECC public  allow to verify if signature is correct.

In case of ethereum transactions there is no public key associated with transaction but it has to be recovered from transaction signature itself.

Recovering ECC public from single ECDSA results in 2 possible public keys to determine which one was used to sign the transaction we have additional value v which is 27 or 28 (after block 3 000 000 it is defined by https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md).
27 and 28 are just arbitrary values picked to represent 2 recovered public keys, base on them reconstruct ephemeral public key base on r (to do that we are using spongy castle library and translate v to recovery id 28 is 3 and 27 is 2).

Recovery formula is:
Q = r^(-1)(sR - eG)

Q is public key that can be used after encoding to calculate transaction sender address and R is recovered ephemeral key, e is hash of transaction encoded as big integer, r^(-1) is modulo inverse of r,
sR is point wise multiplication of point R by scalar s
eG is point wise multiplication of point G (specific to cureve used for ethereum) by scalar s which is integer representation of hash of message that was signed (RLP encoded transaction)

Ours implementation of ECDSA recovery is here (it includes changes from EIP-155): https://github.com/input-output-hk/mantis/blob/master/src/main/scala/io/iohk/ethereum/crypto/ECDSASignature.scala

Transaction address is calculated as 20 right most bytes of kec256(encoded(q))

Transaction is prepared for signing by RLP encoiding its fields and hashing the resulted byte array with kec256, specific fields for encoding are defined in yellow paper, but they changed after EIP-155 (this EIP does not have target block but in geth and parity target block is set to 3 000 000)