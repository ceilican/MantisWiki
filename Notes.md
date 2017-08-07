Running fast sync and switching to regular sync before fast sync completes can result in an exception, 

`Node not found e2897f4b27f665d686dc46799445b583ad1220c15b1f8eaf2d590f90fd5e6c10, trie is inconsistent`

Clean the db and restart. 

### Keys exported from MyEtherWallet

When exporting a keyfile from MyEtherWallet, one of the fields in json is capitalized (`"Crypto": {...}`). We expect all fields to be lowercase and fail to read this file.
Work around: edit the file and change all keys to lowercase (`"Crypto"` -> `"crypto"`).