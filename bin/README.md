# bin package
This package contains 3 binaries:
- `kardia-rpc`: service that connects to Kardia P2P network.
- `kardia-sentry`: service that connects the node to the p2p network of the blockchain. `core` and  `consensus` subcribe to this service for further processings. Read more about [sentry](../packages/sentry/README.md).
- `kardia`: the heaviest service that contains `tx_pool`, `downloader` (connects to BitTorrent P2P network) daemon.
  - Inits db
  - Init consensus engine
  - It adds all `kardia-sentry` in the configuration to the node instance (defined in `p2p/node`).
    - Node `start_sync()`: start syncing via `sentry`. Read more about [p2p/node](../packages/sentry/README.md)
  - Set up staged sync queues
    - Add stages
    - Run stagedsync process