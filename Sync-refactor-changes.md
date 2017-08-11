1. Extract fast and regular sync from SyncController into separate child actors
- easier to manage and cleaner code
- clear distinction between the two modes and the logic in them
2. Change request handlers (FastSyncReceiptsRequestHandler etc) so that they forward the result to sync actor instead of handling the queuing logic.
- the logic is different for fast and regular sync (see for example `SyncBlockHeadersRequestHandler`, it sends `EnqueueBlockBodies` which is not used in RegularSync at all)
- easier to reason about
3. Do we still need to periodically ask PeerManager for peers (`scheduler.schedule(0.seconds, peersScanInterval, etcPeerManager, EtcPeerManagerActor.GetHandshakedPeers)`)? maybe we could just listen to PeerHandshaked/PeerDisconnected events and keep the list updated based on them?
- potentially a tiny bit faster
- thanks to event bus (which is already in place) we can remove coupling with peer manager