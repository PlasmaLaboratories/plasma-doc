---
description: >-
  Connect to the Plasma network using supported RPC endpoints and network
  configurations.
---

# Connect to a Network

## Plasma Development Setup

Plasma Node officially supports development on Ubuntu. Other operating systems may still work, but the Plasma team may be unable to support certain questions.

### Installation

#### Docker, Java, and SBT

1. Install [Docker](https://docs.docker.com/engine/install/).
   1. Be sure to follow the Linux post-installation [steps](https://docs.docker.com/engine/install/linux-postinstall/), namely run `sudo usermod -aG docker $USER`
2. Install Java and SBT using [SDKMAN](https://sdkman.io/install).
   1. Prerequisite: Install zip and unzip `sudo apt install zip unzip`
   2. Run `curl -s "https://get.sdkman.io" | bash`
   3. Run `source "$HOME/.sdkman/bin/sdkman-init.sh"`
   4. Run `sdk install java 11.0.17-tem`
   5. Run `sdk install sbt 1.7.3`

### Plasma Node

* Run `git clone` [`https://github.com/PlasmaLaboratories/plasma-node`](https://github.com/PlasmaLaboratories/plasma-node)  and checkout branch `dev`.
* Run `sbt compile` from the command line.
