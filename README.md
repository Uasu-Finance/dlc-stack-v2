# dlc-stack

![build workflow](https://github.com/dlc-link/dlc-stack/actions/workflows/docker-build.yml/badge.svg)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

It is composed of multiple modules that work together to provide a seamless lending experience for DLC.Link stack.

## Modules

### Oracle

The `oracle` module is providing a numeric oracle implementation for bitcoin. (creating events / announcements / attestations).

### Oracle-discovery

The `oracle-discovery` module is responsible for discovering and registering oracles on the network. It provides an API for finding and connecting to available oracles.

## Wallet backend
The wallet module is responsible for communicating with the dlc-manager and oracle. It provides an API for creating and managing loan transactions.

### Storage-API

The `storage-api `module provides an API for hiding storage operations. Currently, it is implemented to work with Postgres as the underlying storage engine.

### Clients

The `clients` module provies re-usable clients for the oracle / wallet / storage-api.

### IT

The it module provides basic integration tests using BDD (Behavior-Driven Development) with Cucumber.

## Build

```bash
make build
```

## Known Build Errors

On Apple silicon (M1, M2) there are some known difficulties building the diesel package. This may materialize as something like the following:
```bash
  = note: ld: warning: directory not found for option '-L/usr/local/lib/postgresql@14'
          ld: library not found for -lpq
          clang: error: linker command failed with exit code 1 (use -v to see invocation)
```
Running the build in the following way may solve this problem. `RUSTFLAGS='-L /opt/homebrew/opt/libpq/lib' cargo build`

The following thread discusses in more details.
https://github.com/diesel-rs/diesel/issues/2605



## License

APM 2.0
