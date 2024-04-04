# gh-attestation

**NOTE**: this repository is now archived as the `gh-attestation` 
extension has been integrated in the `gh` CLI as a core command. Upgrade at least [v2.47.0](https://github.com/cli/cli/releases/tag/v2.47.0) to use the `attestation` command. See the [build provenance private beta documentation](https://github.com/github-early-access/build-provenance-private-beta?tab=readme-ov-file#step-2-verify-the-signature) for more information on using the command.

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

## Trust root management

GitHub is relying on [TUF](https://theupdateframework.io/) to securely
deliver the trust root for our signing authority. It's natively
integrated into the GitHub CLI [attestation extension](https://github.com/github-early-access/gh-attestation/). By using TUF the client will
automatically update the trust root and verify that the local cache is
both up-to-date and valid.

Any client will come with a `root.json` file embedded. Once invoked
the client creates a local cache in
`~/.sigstore/root/tuf-repo.github.com`. If the local cache is removed,
it will be recreated upon next invocation of any client.

The actual TUF repository is located at
`https://tuf-repo.github.com`. The repository is not indexed, but some
important files are:
* [1.root.json](https://tuf-repo.github.com/1.root.json)
* [timestamp.json](https://tuf-repo.github.com/timestamp.json)

You can at any point in time verify that the published repository, or
the local cache is valid by running the following command.

```shell
$ gh attestation tuf-root-verify --mirror https://tuf-repo.github.com --root /path/to/1.root.json
Successfully verified the TUF repository
```

The initial [root.json](tuf/1.root.json) is also available from this
repository.
