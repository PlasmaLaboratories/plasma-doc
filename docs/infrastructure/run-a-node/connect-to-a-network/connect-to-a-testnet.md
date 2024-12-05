# Connect to a Testnet

Run the Plasma Node on the Plasma Genesis Testnet.

### Prerequisites



### gRPC Endpoint

https://testnet.topl.co:443

### P2P

https://testnet.topl.co:9085

### Connect using Docker

In this example, we will be using Docker to run the node.

Connecting to a testnet is by adding it as a known peer. To do this via CLI, you can use `--knownPeers testnet.topl.co:9085`.&#x20;

You will also need to pass the `--config` which contains the genesis block information and other configuration requirements for the given testnet.

The testnet configs are hosted on GitHub which can be automatically downloaded by Bifrost using the `--config` [`https://github.com/PlasmaLaboratories/plasma-genesis-testnets/blob/main/testnet/config.yaml`](https://github.com/PlasmaLaboratories/plasma-genesis-testnets/blob/main/testnet/config.yaml)parameter.

### A full example of connecting to the node:

To run the node in the background, mount `node` the folder into `/tmp/node` to keep persistent data&#x20;

{% code overflow="wrap" %}
```bash
docker run -d -v ./node:/tmp/node ghcr.io/plasmalaboratories/plasma-node:dev 
--disable-indexer --known-peers testnet.plasmalabs.tech:9085 \
--config https://github.com/PlasmaLaboratories/plasma-genesis-testnets/blob/main/testnet/config.yaml
```
{% endcode %}

### Show running node container&#x20;

```
docker ps
```

