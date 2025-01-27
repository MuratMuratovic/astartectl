# astartectl

Command line utility to manage Astarte

## Installation

`astartectl` requires at least Go 1.17.

### Using homebrew

If you are using [homebrew](https://brew.sh/) on your system, you can install `astartectl` out of its tap:

```bash
brew tap astarte-platform/astarte
brew update
brew install astartectl
```

### Using binaries from Github Release

You can download latest `astartectl` binaries for all platforms from [GitHub Releases](https://github.com/astarte-platform/astartectl/releases).

Move the binaries to your `$PATH` folder or set your `$PATH` to the folder where `astartectl` is run from.

## Configuration

`astartectl` works with a context-based configuration. If you are familiar with how `kubectl` works, you'll
find most of its concepts in `astartectl` configuration system. There are two main entities in `astartectl`
configuration: `cluster` and `context`.

A `cluster` represents an Astarte Cluster. It might contain housekeeping credentials, but most of all it should
bear the API URLs necessary to interact with the cluster. `astartectl config clusters` allows you to manipulate
available clusters.

A `context` represents a configuration for `astartectl`, which references a `cluster` and, optionally an Astarte
Realm. A `context` with no realm associated is meant to interact with Housekeeping (for, e.g., creating a Realm).
`astartectl config contexts` allows you to manipulate available clusters.

### Active context

At any time, when invoking `astartectl` without any further configuration options, the active `context` will be
used. There is only one context available at a time, which can be queried by issuing `astartectl config current-context`.
The context can be changed at any time using `astartectl config set-current-context`.

### Fetching context information

In most cases, if you have access to the Kubernetes Cluster hosting your Astarte Cluster, you will be able to
automatically build the `cluster` entry in the configuration. This can be done through the
`astartectl cluster instances get-cluster-config` command, which creates a `cluster` entry based on the Astarte
instance installed on the Kubernetes cluster referenced by your current `kubectl` context, if any.

In the same fashion, creating a new Realm automatically creates a new configuration `context`, if a private
key and all necessary information are provided.

## Usage

Run `astartectl` to see available commands.
