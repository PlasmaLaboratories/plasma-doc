---
description: >-
  Connect to the Plasma network using supported RPC endpoints and network
  configurations.
---

# Connect to a Network

## Plasma Development Setup

Plasma Node officially supports development on Ubuntu. Other operating systems may still work, but the Plasma team may be unable to support certain questions.

### Installation

* Install [Docker](https://docs.docker.com/engine/install/).

{% hint style="info" %}
Be sure to follow the Linux post-installation [steps](https://docs.docker.com/engine/install/linux-postinstall/), namely run `sudo usermod -aG docker $USER`
{% endhint %}

* Install Java and SBT using [SDKMAN](https://sdkman.io/install).
* Install zip and unzip `sudo apt install zip unzip`

## Plasma Node Setup Commands

Enter the following commands in your terminal

```
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install java 11.0.17-tem
sdk install sbt 1.7.3
git clone https://github.com/PlasmaLaboratories/plasma-node
git checkout branch main
sbt compile
```



