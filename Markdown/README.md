# Proptrack Daily Export Build
[![Build status](https://badge.buildkite.com/6921b9d3b8a812e3c7a401953ee69ba500fe413bb6d20ac821.svg?branch=master)](https://buildkite.com/rea/proptrack-daily-export-build)
[![One Pager](https://1badge.reainternal.net/systems_health/1pager.svg)](docs/1pager.md)

## Development

Log into Cowbell, before running the following:

### Run your Breeze instance locally

Please refer to [Breeze docs](https://pages.git.realestate.com.au/data-platform/breeze/dev-environment/) for more info.

```shell script
./auto/breeze-up
```

### Spin down your local Breeze instance

```shell script
./auto/breeze-down
```

## Test with Breeze CLI

Read more about the Breeze CLI in the [Breeze CLI docs](https://pages.git.realestate.com.au/data-platform/breeze/usage/)

Log into REA Artifacts ECR and Cowbell. Then, pull the latest, required Docker images.
```shell script
./auto/refresh-images
```

### YAML lint

```shell script
./auto/breeze lint yaml
```

For the following commands, you will need access to the VPN and to be authenticated as the AWS role `Vault-Breeze-Tester`. More info is here in the [docs](https://pages.git.realestate.com.au/data-platform/breeze/configuration/testing-dags/#scripts).

### SQL files

```shell script
./auto/breeze test sql
```

### UDFs

```shell script
./auto/breeze test udfs
```
