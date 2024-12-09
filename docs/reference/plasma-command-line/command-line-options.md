# Command line options

Plasma accepts the following command line arguments:

<pre><code><strong>  --cli &#x3C;bool>                       An optional flag to run the CLI/Shell instead of regular node
</strong>                                     operations.
  --config &#x3C;str>                     Zero or more config files (.conf, .json, .yaml) to apply to the
                                     node. Config files stack such that the last config file takes
                                     precedence. To specify an internal resource, prefix the value
                                     with "resource://".
  --dataDir &#x3C;str>                    The directory to use when saving/reading blockchain data
  --databaseType &#x3C;str>               The type of data storage to use. Valid options: `levelDb-jni`
                                     (default), `levelDb-java`
  --debug                            An optional flag to enable debug mode on this node.
  --disableGenus                     Disables the Genus server and Genus gRPC services
  --idle &#x3C;bool>                      An optional flag to run in no-op mode. The application will sit
                                     idle until terminated. This is useful for creating backups of
                                     the node's data.
  --knownPeers &#x3C;str>                 A comma-delimited list of host:port values to connect to at
                                     launch (i.e. 1.2.3.4:9084,5.6.7.8:9084)
  --logbackFile &#x3C;str>                An optional path to a logback.xml file to override the logging
                                     configuration of the node.
  --orientDbDir &#x3C;str>                The directory to use when saving/reading graph data
  --orientDbPassword &#x3C;str>           The password to use when connecting to OrientDB
  --p2pBindHost &#x3C;str>                The hostname to bind to for the P2P layer (i.e. localhost or
                                     0.0.0.0)
  --p2pBindPort &#x3C;int>                The port to bind to for the P2P layer (i.e. 9084)
  --p2pPublicHost &#x3C;str>              The hostname to bind for incoming connections for the P2P layer
                                     (i.e. localhost or 0.0.0.0)
  --p2pPublicPort &#x3C;int>              The port to bind for incoming connections for the P2P layer
                                     (i.e. 9084)
  --rewardAddress &#x3C;LockAddress>      The reward address for block production
  --rpcBindHost &#x3C;str>                The hostname to bind to for the RPC layer (i.e. localhost or
                                     0.0.0.0)
  --rpcBindPort &#x3C;int>                The port to bind to for the RPC layer (i.e. 9085)
  --stakingAddress &#x3C;StakingAddress>  The staking address for block production
  --stakingDir &#x3C;str>                 The directory of the block producer's staking keys
  --testnetStakerCount &#x3C;int>         The number of stakers to initialize.
  --testnetStakerIndex &#x3C;int>         The index of the staker to launch.
  --testnetTimestamp &#x3C;long>          A UTC Unix epoch timestamp (ms) to use when seeding a private
                                     testnet.
</code></pre>

You may also view `sbt "node/run --help"` for more information.
