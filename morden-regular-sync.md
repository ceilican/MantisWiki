* Sync was started on EC2
* Got error while executing block 619153 there was difference in gas consumed by contract it was fixed (it was related to big memory address being converted to 32 bit int)
* EC2 run out of disk space, restarted with more disk space attached
* got stack overflow error because of to small stack size pre JVM process in transaction that was calling recursively subcontract
* got failure in block 1805823 - wrong gas consumed (it was fixed)
* EC2 fully synced