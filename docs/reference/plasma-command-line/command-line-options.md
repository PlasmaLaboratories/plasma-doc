---
description: Command line options to interact with the Plasma node.
---

# Command line options

Plasma accepts the following command line arguments:



```
  --block-regtest-permission <bool>    Enables a testing mode for the node.
  --cli <bool>                         An optional flag to run the CLI/Shell instead of regular node
                                       operations.
  --config <str>                       Zero or more config files (.conf, .json, .yaml) to apply to
                                       the node. Config files stack such that the last config file
                                       takes precedence. To specify an internal resource, prefix the
                                       value with "resource://".
  --data-dir <str>                     The directory to use when saving/reading blockchain data
  --database-type <str>                The type of data storage to use. Valid options: `levelDb-jni`
                                       (default), `levelDb-java`
  --debug                              An optional flag to enable debug mode on this node.
  --disable-indexer                    Disables the Indexer server and Indexer gRPC services
  --ethereum-json-rpc-bind-host <str>  The hostname to bind to for the Ethereum JSON-RPC layer (i.e.
                                       localhost or 0.0.0.0)
  --ethereum-json-rpc-bind-port <int>  The port to bind to for the Ethereum JSON-RPC layer (i.e.
                                       8545)
  --idle <bool>                        An optional flag to run in no-op mode. The application will
                                       sit idle until terminated. This is useful for creating
                                       backups of the node's data.
  --known-peers <str>                  A comma-delimited list of host:port values to connect to at
                                       launch (i.e. 1.2.3.4:9084,5.6.7.8:9084)
  --logback-file <str>                 An optional path to a logback.xml file to override the
                                       logging configuration of the node.
  --orient-db-dir <str>                The directory to use when saving/reading graph data
  --orient-db-password <str>           The password to use when connecting to OrientDB
  --p-2p-bind-host <str>               The hostname to bind to for the P2P layer (i.e. localhost or
                                       0.0.0.0)
  --p-2p-bind-port <int>               The port to bind to for the P2P layer (i.e. 9085)
  --p-2p-public-host <str>             The hostname to bind for incoming connections for the P2P
                                       layer (i.e. localhost or 0.0.0.0)
  --p-2p-public-port <int>             The port to bind for incoming connections for the P2P layer
                                       (i.e. 9084)
  --prune-dir <str>                    Path to pruned data folder. NODE WILL RUN IN DATASTORES PRUNE
                                       MODE if that path is defined (unless running in idle mode is
                                       already defined)
  --reward-address <LockAddress>       The reward address for block production
  --rpc-bind-host <str>                The hostname to bind to for the RPC layer (i.e. localhost or
                                       0.0.0.0)
  --rpc-bind-port <int>                The port to bind to for the RPC layer (i.e. 9084)
  --staking-address <StakingAddress>   The staking address for block production
  --staking-dir <str>                  The directory of the block producer's staking keys
  --testnet-staker-count <int>         The number of stakers to initialize.
  --testnet-staker-index <int>         The index of the staker to launch.
  --testnet-timestamp <long>           A UTC Unix epoch timestamp (ms) to use when seeding a private
                                       testnet.
```

You may also view `sbt "node/run --help"` for more information.
