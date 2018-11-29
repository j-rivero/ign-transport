# Ignition Gazebo : A Robotic Simulator

**Maintainer:** caguero AT openrobotics.org

[![Bitbucket open issues](https://img.shields.io/bitbucket/issues-raw/ignitionrobotics/ign-transport.svg)](https://bitbucket.org/ignitionrobotics/ign-transport/issues)
[![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/ignitionrobotics/ign-transport.svg)](https://bitbucket.org/ignitionrobotics/ign-transport/pull-requests)
[![Discourse topics](https://img.shields.io/discourse/https/community.gazebosim.org/topics.svg)](https://community.gazebosim.org)
[![Hex.pm](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)

Build | Status
-- | --
Test coverage | [![codecov](https://codecov.io/bb/ignitionrobotics/ign-transport/branch/default/graph/badge.svg)](https://codecov.io/bb/ignitionrobotics/ign-transport)
Ubuntu Bionic | [![Build Status](https://build.osrfoundation.org/buildStatus/icon?job=ignition_transport-ci-default-bionic-amd64)](https://build.osrfoundation.org/job/ignition_transport-ci-default-bionic-amd64)
Homebrew      | [![Build Status](https://build.osrfoundation.org/buildStatus/icon?job=ignition_transport-ci-default-homebrew-amd64)](https://build.osrfoundation.org/job/ignition_transport-ci-default-homebrew-amd64)
Windows       | [![Build Status](https://build.osrfoundation.org/buildStatus/icon?job=ignition_transport-ci-default-windows7-amd64)](https://build.osrfoundation.org/job/ignition_transport-ci-default-windows7-amd64)

Ignition transport is a component in the ignition framework, a set
of libraries designed to rapidly develop robot applications.

  [http://ignitionrobotics.org](http://ignitionrobotics.org)

# Table of Contents

[Features](#markdown-header-features)

[Install](#markdown-header-install)

* [Binary Install](#markdown-header-binary-install)

* [Source Install](#markdown-header-source-install)

[Usage](#markdown-header-usage)

[Documentation](#markdown-header-documentation)

[Testing](#markdown-header-testing)

[Folder Structure](#markdown-header-folder-structure)

[Code of Conduct](#markdown-header-code-of-conduct)

[Contributing](#markdown-header-code-of-contributing)

[Versioning](#markdown-header-versioning)

[License](#markdown-header-license)

# Features

Ignition Transport is an open source communication library that allows sharing
data between clients. In our context, a client is called a node. Nodes might be
running within the same process in the same machine or in machines located in
different continents. Ignition Transport is multi-platform (Linux, Mac OS X, and
Windows), so all the low level details, such as data alignment or endianness are
hidden for you.

Ignition Transport uses Google Protocol buffers as the data type for
communicating between nodes. Users can define their own messages using the
Protobuf utils, and then, exchange them between the nodes. Ignition Transport
discovers, serializes and delivers messages to the destinations using a
combination of custom code and ZeroMQ.

# Install

We recommend following the [Binary Install](#markdown-header-binary-install)
instructions to get up and running as quickly and painlessly as possible.

The [Source Install](#markdown-header-source-install) instructions should be
used if you need the very latest software improvements, you need to modify the
code, or you plan to make a contribution.

## Binary Install

On Ubuntu systems, `apt-get` can be used to install `ignition-transport`:

```
$ sudo apt install libignition-transport<#>-dev
```

Be sure to replace `<#>` with a number value, such as `1` or `2`, depending on
which version you need.

## Source Install

See the [install](https://ignitionrobotics.org/tutorials/transport/5.0/md__data_ignition_ign-transport_tutorials_02_installation.html)
section of the documentation.

# Usage

See [tutorials](https://ignitionrobotics.org/tutorials/transport/5.0/index.html)
and the [example directory](https://bitbucket.org/ignitionrobotics/ign-transport/raw/default/example/?at=default)
in the source code.

# Documentation

Visit the [documentation page](https://ignitionrobotics.org/api/transport/6.0/index.html).

## Build documentation

```
cd build
make doc
```

Upload documentation to ignitionrobotics.org.

```
cd build
sh upload.sh
```

If you're creating a new release, then tell ignitionrobotics.org about
   the new version. For example:

```
curl -k -X POST -d '{"libName":"transport", "version":"1.0.0", "releaseDate":"2017-10-09T12:10:13+02:00","password":"secret"}' https://api.ignitionrobotics.org/1.0/versions
```

# Testing

Tests can be run by building the `test` target. From your build directory you
can run:

```
$ make test
```

# Folder Structure

* `conf`: Configuration file for the integration with the `ign` CLI tool.
* `example`: Example programs that use most of the Ignition Transport API.
* `include`: C++ utility header files that get installed with
`ignition-transport`.
* `log`: All the code related with Ignition Transport logging.
* `src`: Source code of the core library.
* `test`: A directory of tests for the C++ utility component of
`ignition-transport`.
* `tools`: Scripts for continuous integration testing.
* `tutorials`: A set of tutorials about Ignition Transport features.

# Contributing

Please see
[CONTRIBUTING.md](https://bitbucket.org/ignitionrobotics/ign-gazebo/src/406665896aa40bb42f14cf61d48b3d94f2fc5dd8/CONTRIBUTING.md?at=default&fileviewer=file-view-default).

# Code of Conduct

Please see
[CODE_OF_CONDUCT.md](https://bitbucket.org/ignitionrobotics/ign-gazebo/src/406665896aa40bb42f14cf61d48b3d94f2fc5dd8/CODE_OF_CONDUCT.md?at=default&fileviewer=file-view-default).

# Versioning

This library uses [Semantic Versioning](https://semver.org/). Additionally,
this library is part of the [Ignition Robotics project](https://ignitionrobotics.org)
which periodically releases a versioned set of compatible and complimentary
libraries. See the [Ignition Robotics website](https://ignitionrobotics.org) for
version and release information.

# License

This library is licensed under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0).
See also the [LICENSE]https://bitbucket.org/ignitionrobotics/ign-transport/raw/default/LICENSE)
file.
