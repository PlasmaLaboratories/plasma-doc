# Connect using Docker

In this example, we will be using Docker to run the node.

To connect to a network you add it to a known peer. To do this via CLI, you use `--knownPeers testnet.plasmalabs.tech:9085.`&#x20;

You will also need to pass the `--config` flag which contains the genesis block information and other configuration requirements for the given network.

### Start Plasma Node

{% hint style="info" %}
To run the node in the background. Mount `node` folder into `/tmp/node` to keep persistent data&#x20;
{% endhint %}

The network configurations are available on GitHub and can be automatically downloaded by Plasma based on the selected network.

{% tabs %}
{% tab title="Devnet" %}
```
docker run  -d -v ./node:/tmp/node ghcr.io/plasmalaboratories/plasma-node:dev 
--disable-indexer --known-peers devnet.plasmalabs.tech:9085 \
--config https://github.com/PlasmaLaboratories/plasma-genesis-testnets/blob/main/devnet/config.yaml
```
{% endtab %}

{% tab title="Testnet" %}
```
docker run -d -v ./node:/tmp/node ghcr.io/plasmalaboratories/plasma-node:dev 
--disable-indexer --known-peers testnet.plasmalabs.tech:9085 \
--config https://github.com/PlasmaLaboratories/plasma-genesis-testnets/blob/main/testnet/config.yaml
```


{% endtab %}

{% tab title="Mainnet" %}
Coming soon!
{% endtab %}

{% tab title="Private Network" %}
Coming Soon.
{% endtab %}
{% endtabs %}

### Show running node container&#x20;

```
docker ps
```
