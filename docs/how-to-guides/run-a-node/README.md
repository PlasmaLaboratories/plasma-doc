# Run a Node

## Plasma Network Full Node

The Plasma node is the reference implementation of a full node running the Plasma protocol. The Plasma protocol enables a new, more inclusive, and sustainable economy through purpose-built blockchain technology.

### Releases

Begin interacting with Plasma protocol using the latest `Plasma-node` client available under [Releases](https://github.com/PlasmaLaboratories/plasma-node/releases/latest). Docker containers for each release are available via the [Github Container Repository](https://github.com/PlasmaLaboratories/plasma-node)[ ](https://github.com/PlasmaLaboratories/plasma-node)and [Docker Hub](https://hub.docker.com/r/stratalab/plasma-node/tags). We encourage all production deployments of Plasma node to make use of our Docker releases.

#### Release Versioning

Tetra-eon releases of Plasma are currently versioned on an incrementing beta version (i.e. `2.0.0-beta0`, `2.0.0-beta1`). Once the implementation reaches a stable point, we will adopt [semantic versioning](https://semver.org/) concerning the protocol consensus mechanism. We chose to use semantic versioning because blockchains must maintain strict binary compatibility with all previous consensus, application, and network messages to allow trustless bootstrapping of new network participants from Genesis.

We apply the following rules to our MAJOR.MINOR.PATCH versions:

* `MAJOR` the index reflects hard forks or substantial network upgrades requiring significant community coordination
* `MINOR` the index captures soft forks, and may include breaking API changes (to any module within the Plasma monorepo) or significant new feature introductions
* `PATCH` index indicates non-breaking changes and bug fixes

### Getting Started

Please read our [setup instructions](./) for a step-by-step guide to installing and running a Plasma node. At this time, **we officially support the use of Debian-based distributions such as Ubuntu only**.&#x20;

While other platforms may function with additional effort, our documentation does not explicitly consider these targets.

### Running a Node

There a are two major ways of running a Plasma node either through the Bare metal approach or Docker.

### Testing

{% hint style="info" %}
**Note**

These instructions assume a working development environment.
{% endhint %}

To run the Plasma unit test suite from the project directory: `sbt test`

To publish a Docker image from the project directory for local testing: `sbt node/Docker/publishLocal`.&#x20;

To use the locally published image, run `docker runghcr.io/plasmalaboratories/plasma-node:dev`.

