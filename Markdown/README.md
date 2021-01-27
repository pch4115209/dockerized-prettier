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

| Name                                                                            | Resolution                                                                                                                                                                                                             | Note                                                                                               |
| ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [Comps Build] proc_validateDailyListingsAndAuctions Fail at YYYY mm:ss - ERROR  | This is caused by 0 listing ingested on the day. To verify it, 1). Check Proptrack-daily-export-build DAG 2). Log on Listing Prod Server or/and Comps Build Server to check tables `data_listings` and `data_auctions` | This Alarm is not auto resolvable and will result in **blocking** job in PT side.                  |
| Comps Build] proc_validateDailyListingsAndAuctions Fail at YYYY mm:ss - WARNING | This is can be caused by 1). listing threshold check (+-30% of prev days listings) 2). listing rolling week threshold check (+-30% of same period last year) 3). listing auction volume check (>0)                     | This is not auto resolvabl, and this warning alarm will **NOT** result in blocking job in PT side. |
