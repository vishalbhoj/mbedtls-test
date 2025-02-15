# Mbed TLS CI

Out of source test infrastructure information for Mbed TLS.

When raising a PR in [mbedtls](https://github.com/ARMmbed/mbedtls) a range of tests will be run automatically. This repository contains all the information required to reproduce these tests. This can be particularly useful for reproducing failures on a PR.

The docker files in `resources/docker_files` are the ones used by the CI. For more information see the corresponding readme: `resources/docker_files/README.md`.

## Quick Start

To get the docker image used in the CI, run the following command from the root of a fresh checkout of the `master` branch of this repository:
```sh
docker pull trustedfirmware/ci-amd64-mbed-tls-ubuntu:ubuntu-16.04-$(git hash-object resources/docker_files/ubuntu-16.04/Dockerfile)
```
Then to run the image:
```sh
./resources/docker_files/run.sh <mount dir> trustedfirmware/ci-amd64-mbed-tls-ubuntu:ubuntu-16.04-$(git hash-object resources/docker_files/ubuntu-16.04/Dockerfile)
```
Where `<mount dir>` is a directory from the host that will be mounted on the container at startup (usually a local checkout of Mbed TLS).

If `<mount dir>` is the root of an Mbed TLS source tree, the tests can be run with:
```sh
./tests/scripts/all.sh --no-armcc
```

## Contribution

This repository accepts contributions only from Mbed TLS maintainers.

## License

The software is provided under the [Apache 2.0 license](LICENSE) (except for some files which specify a different license).
