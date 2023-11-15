# gh-attestation

**NOTE**: this is the location of the gh-attestation extension during Private Beta and is subject to change once the Private Beta is over.

**OTHER NOTE**: command output in this README may look different from what is in the tool at runtime as we make minor changes.

## Installation
1. Install the [GH CLI tool](https://cli.github.com/)
2. Install this extension:

```shell
╰─$ gh ext install github-early-access/gh-attestation
✓ Installed extension github-early-access/gh-attestation
```

## Upgrading
We will be releasing new versions of the extension throughout the private beta. Upgrade as follows:

```shell
╰─$ gh ext upgrade github-early-access/gh-attestation
[attestation]: upgraded from v0.1.8 to v0.1.16
✓ Successfully upgraded extension
```

## Reporting version
When you file bugs, we will ask you to include a version string so we know what version of the tool you're on:

```shell
╰─$ gh attestation version
7f4f753-0.1.16 (2023-11-14)
```

## Usage
The CLI extension itself offers detailed information about usage.

To see a list of all subcommands:

```shell
╰─$ gh attestation
Work with attestations that represent trusted metadata about artifacts and images

Usage:
  attestation [command]

Available Commands:
  completion  Generate the autocompletion script for the specified shell
  download    Download trusted metadata about a binary artifact for offline use
  help        Help about any command
  verify      Cryptographically verify an artifact
  version     Print version of the tool

Flags:
  -h, --help   help for attestation

Use "attestation [command] --help" for more information about a command.
```

To see detailed usage information for a given subcommand:

`gh attestation help <subcommand>` 
