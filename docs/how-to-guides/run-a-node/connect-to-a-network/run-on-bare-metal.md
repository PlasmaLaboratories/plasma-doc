# Run on Bare Metal

### Ubuntu

### Prerequisites

* Install [SDKMAN](https://sdkman.io/) and [Java](https://www.java.com/download/ie_manual.jsp)

```sh
sudo apt install curl zip unzip
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
sdk install java
```

#### Download and Run Jar

Locate the latest version from [Plasma lastest release](https://github.com/PlasmaLaboratories/plasma-node/releases/latest).&#x20;

## Example:

```sh
wget https://github.com/PlasmaLaboratories/plasma-node/releases/download/dev/plasma-node-0.1.4.jar
```

## Run

```sh
java -jar plasma-node-dev.jar
```
