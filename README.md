# ebola-orderly

[![Build status](https://badge.buildkite.com/e811658780dce01393cd74ba656b728f0656b2de9edfbe2426.svg?branch=master)](https://buildkite.com/mrc-ide/ebola-orderly)

This is the docker container for [ebola-outputs](https://github.com/imperialebola2018/ebola-outputs).  It exists outside that repository because otherwise every new report we use risks dragging in a new LaTeX installation.

This repo is a fork of [`montagu-orderly`](https://github.com/vimc/montagu-orderly) with minor modifications

**Interaction with the server**.  These commands interact with the orderly server on the *same host* as you run it.  If you run these on your desktop they will not affect any other machine.

Make sure you have the most recent version of the container with with

Update the `ebola-output` repo on the orderly volume

```
./pull_sources
```

Run orderly commands with

```
./orderly run <name>
./orderly list names
./orderly --help
```

etc.

Get a shell on the container with

```
./shell
```

## Building the image

The image is built on the [VIMC teamcity server](http://teamcity.montagu.dide.ic.ac.uk:8111/viewType.html?buildTypeId=montagu_Orderly_EbolaOrderly_Build), as it is too large to build on travis now (build times out after an hour).
