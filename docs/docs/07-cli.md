---
sidebar_position: 7
description: Ignite CLI docs.
---

# CLI Reference

Documentation for Ignite CLI.
## ignite

Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain

**Synopsis**

Ignite CLI is a tool for creating sovereign blockchains built with Cosmos SDK, the world’s
most popular modular blockchain framework. Ignite CLI offers everything you need to scaffold,
test, build, and launch your blockchain.

To get started, create a blockchain:

ignite scaffold chain github.com/username/mars

**Options**

```
  -h, --help   help for ignite
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts
* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain
* [ignite completion](#ignite-completion)	 - Generate the autocompletion script for the specified shell
* [ignite docs](#ignite-docs)	 - Show Ignite CLI docs
* [ignite generate](#ignite-generate)	 - Generate clients, API docs from source code
* [ignite node](#ignite-node)	 - Make calls to a live blockchain node
* [ignite relayer](#ignite-relayer)	 - Connect blockchains by using IBC protocol
* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more
* [ignite tools](#ignite-tools)	 - Tools for advanced users
* [ignite version](#ignite-version)	 - Print the current build information


## ignite account

Commands for managing accounts

**Synopsis**

Commands for managing accounts. An account is a pair of a private key and a public key.
Ignite CLI uses accounts to interact with the Ignite blockchain, use an IBC relayer, and more.

**Options**

```
  -h, --help                     help for account
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite account create](#ignite-account-create)	 - Create a new account
* [ignite account delete](#ignite-account-delete)	 - Delete an account by name
* [ignite account export](#ignite-account-export)	 - Export an account as a private key
* [ignite account import](#ignite-account-import)	 - Import an account by using a mnemonic or a private key
* [ignite account list](#ignite-account-list)	 - Show a list of all accounts
* [ignite account show](#ignite-account-show)	 - Show detailed information about a particular account


## ignite account create

Create a new account

```
ignite account create [name] [flags]
```

**Options**

```
  -h, --help   help for create
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite account delete

Delete an account by name

```
ignite account delete [name] [flags]
```

**Options**

```
  -h, --help   help for delete
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite account export

Export an account as a private key

```
ignite account export [name] [flags]
```

**Options**

```
  -h, --help                help for export
      --non-interactive     Do not enter into interactive mode
      --passphrase string   Passphrase to encrypt the exported key
      --path string         path to export private key. default: ./key_[name]
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite account import

Import an account by using a mnemonic or a private key

```
ignite account import [name] [flags]
```

**Options**

```
  -h, --help                help for import
      --non-interactive     Do not enter into interactive mode
      --passphrase string   Passphrase to decrypt the imported key (ignored when secret is a mnemonic)
      --secret string       Your mnemonic or path to your private key (use interactive mode instead to securely pass your mnemonic)
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite account list

Show a list of all accounts

```
ignite account list [flags]
```

**Options**

```
      --address-prefix string   Account address prefix (default "cosmos")
  -h, --help                    help for list
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite account show

Show detailed information about a particular account

```
ignite account show [name] [flags]
```

**Options**

```
      --address-prefix string   Account address prefix (default "cosmos")
  -h, --help                    help for show
```

**Options inherited from parent commands**

```
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite account](#ignite-account)	 - Commands for managing accounts


## ignite chain

Build, initialize and start a blockchain node or perform other actions on the blockchain

**Synopsis**

Commands in this namespace let you to build, initialize, and start your
blockchain node locally for development purposes.

To run these commands you should be inside the project's directory so that
Ignite can find the source code. To ensure that you are, run "ls", you should
see the following files in the output: "go.mod", "x", "proto", "app", etc.

By default the "build" command will identify the "main" package of the project,
install dependencies if necessary, set build flags, compile the project into a
binary and install the binary. The "build" command is useful if you just want
the compiled binary, for example, to initialize and start the chain manually. It
can also be used to release your chain's binaries automatically as part of
continuous integration workflow.

The "init" command will build the chain's binary and use it to initialize a
local validator node. By default the validator node will be initialized in your
$HOME directory in a hidden directory that matches the name of your project.
This directory is called a data directory and contains a chain's genesis file
and a validator key. This command is useful if you want to quickly build and
initialize the data directory and use the chain's binary to manually start the
blockchain. The "init" command is meant only for development purposes, not
production.

The "serve" command builds, initializes, and starts your blockchain locally with
a single validator node for development purposes. "serve" also watches the
source code directory for file changes and intelligently
re-builds/initializes/starts the chain, essentially providing "code-reloading".
The "serve" command is meant only for development purposes, not production.

To distinguish between production and development consider the following.

In production, blockchains often run the same software on many validator nodes
that are run by different people and entities. To launch a blockchain in
production, the validator entities coordinate the launch process to start their
nodes simultaneously.

During development, a blockchain can be started locally on a single validator
node. This convenient process lets you restart a chain quickly and iterate
faster. Starting a chain on a single node in development is similar to starting
a traditional web application on a local server.

The "faucet" command lets you send tokens to an address from the "faucet"
account defined in "config.yml". Alternatively, you can use the chain's binary
to send token from any other account that exists on chain.

The "simulate" command helps you start a simulation testing process for your
chain.


**Options**

```
  -h, --help   help for chain
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite chain build](#ignite-chain-build)	 - Build a node binary
* [ignite chain faucet](#ignite-chain-faucet)	 - Send coins to an account
* [ignite chain init](#ignite-chain-init)	 - Initialize your chain
* [ignite chain serve](#ignite-chain-serve)	 - Start a blockchain node in development
* [ignite chain simulate](#ignite-chain-simulate)	 - Run simulation testing for the blockchain


## ignite chain build

Build a node binary

**Synopsis**


The build command compiles the source code of the project into a binary and
installs the binary in the $(go env GOPATH)/bin directory.

You can customize the output directory for the binary using a flag:

  ignite chain build --output dist

To compile the binary Ignite first compiles protocol buffer (proto) files into
Go source code. Proto files contain required type and services definitions. If
you're using another program to compile proto files, you can use a flag to tell
Ignite to skip the proto compilation step:

  ignite chain build --skip-proto

Afterwards, Ignite install dependencies specified in the go.mod file. By default
Ignite doesn't check that dependencies of the main module stored in the module
cache have not been modified since they were downloaded. To enforce dependency
checking (essentially, running "go mod verify") use a flag:

  ignite chain build --check-dependencies

Next, Ignite identifies the "main" package of the project. By default the "main"
package is located in "cmd/{app}d" directory, where "{app}" is the name of the
scaffolded project and "d" stands for daemon. If your your project contains more
than one "main" package, specify the path to the one that Ignite should compile
in config.yml:

build:
  main: custom/path/to/main

By default the binary name will match the top-level module name (specified in
go.mod) with a suffix "d". This can be customized in config.yml:

build:
  binary: mychaind

You can also specify custom linker flags:

build:
  ldflags:
    - "-X main.Version=development"
    - "-X main.Date=01/05/2022T19:54"

To build binaries for a release, use the --release flag. The binaries for one or
more specified release targets are built in a "release/" directory in the
project's source directory. Specify the release targets with GOOS:GOARCH build
tags. If the optional --release.targets is not specified, a binary is created
for your current environment.

  ignite chain build --release -t linux:amd64 -t darwin:amd64 -t darwin:arm64


```
ignite chain build [flags]
```

**Options**

```
      --check-dependencies        verify that cached dependencies have not been modified since they were downloaded
      --clear-cache               clear the build cache (advanced)
  -h, --help                      help for build
  -o, --output string             binary output path
  -p, --path string               path of the app (default ".")
      --proto-all-modules         enables proto code generation for 3rd party modules used in your chain. Available only without the --release flag
      --release                   build for a release
      --release.prefix string     tarball prefix for each release target. Available only with --release flag
  -t, --release.targets strings   release targets. Available only with --release flag
      --skip-proto                skip file generation from proto
  -v, --verbose                   verbose output
```

**SEE ALSO**

* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain


## ignite chain faucet

Send coins to an account

```
ignite chain faucet [address] [coin<,...>] [flags]
```

**Options**

```
  -h, --help          help for faucet
      --home string   home directory used for blockchains
  -p, --path string   path of the app (default ".")
  -v, --verbose       Verbose output
```

**SEE ALSO**

* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain


## ignite chain init

Initialize your chain

**Synopsis**

The init command compiles and installs the binary (like "ignite chain build")
and uses that binary to initialize the blockchain's data directory for one
validator. To learn how the build process works, refer to "ignite chain build
--help".

By default, the data directory will be initialized in $HOME/.mychain, where
"mychain" is the name of the project. To set a custom data directory use the
--home flag or set the value in config.yml:

init:
  home: "~/.customdir"

The data directory contains three files in the "config" directory: app.toml,
config.toml, client.toml. These files let you customize the behavior of your
blockchain node and the client executable. When a chain is re-initialized the
data directory can be reset. To make some values in these files persistent, set
them in config.yml:

init:
  app:
    minimum-gas-prices: "0.025stake"
  config:
    consensus:
      timeout_commit: "5s"
      timeout_propose: "5s"
  client:
    output: "json"

The configuration above changes the minimum gas price of the validator (by
default the gas price is set to 0 to allow "free" transactions), sets the block
time to 5s, and changes the output format to JSON. To see what kind of values
this configuration accepts see the generated TOML files in the data directory.

As part of the initialization process Ignite creates on-chain accounts with
token balances. By default, config.yml has two accounts in the top-level
"accounts" property. You can add more accounts and change their token balances.
Refer to config.yml guide to see which values you can set.

One of these accounts is a validator account and the amount of self-delegated
tokens can be set in the top-level "validator" property.

One of the most important components of an initialized chain is the genesis
file, the 0th block of the chain. The genesis file is stored in the data
directory "config" subdirectory and contains the initial state of the chain,
including consensus and module parameters. You can customize the values of the
genesis in config.yml:

genesis:
  app_state:
    staking:
      params:
        bond_denom: "foo"

The example above changes the staking token to "foo". If you change the staking
denom, make sure the validator account has the right tokens.

The init command is meant to be used ONLY FOR DEVELOPMENT PURPOSES. Under the
hood it runs commands like "appd init", "appd add-genesis-account", "appd
gentx", and "appd collect-gentx". For production, you may want to run these
commands manually to ensure a production-level node initialization.


```
ignite chain init [flags]
```

**Options**

```
      --check-dependencies   verify that cached dependencies have not been modified since they were downloaded
      --clear-cache          clear the build cache (advanced)
  -h, --help                 help for init
      --home string          home directory used for blockchains
  -p, --path string          path of the app (default ".")
      --skip-proto           skip file generation from proto
```

**SEE ALSO**

* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain


## ignite chain serve

Start a blockchain node in development

**Synopsis**

Start a blockchain node with automatic reloading

```
ignite chain serve [flags]
```

**Options**

```
      --check-dependencies   verify that cached dependencies have not been modified since they were downloaded
      --clear-cache          clear the build cache (advanced)
  -c, --config string        Ignite config file (default: ./config.yml)
  -f, --force-reset          Force reset of the app state on start and every source change
  -h, --help                 help for serve
      --home string          home directory used for blockchains
  -p, --path string          path of the app (default ".")
      --proto-all-modules    enables proto code generation for 3rd party modules used in your chain
  -r, --reset-once           Reset of the app state on first start
      --skip-proto           skip file generation from proto
  -v, --verbose              Verbose output
```

**SEE ALSO**

* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain


## ignite chain simulate

Run simulation testing for the blockchain

**Synopsis**

Run simulation testing for the blockchain. It sends many randomized-input messages of each module to a simulated node and checks if invariants break

```
ignite chain simulate [flags]
```

**Options**

```
      --blockSize int             operations per block (default 30)
      --exportParamsHeight int    height to which export the randomly generated params
      --exportParamsPath string   custom file path to save the exported params JSON
      --exportStatePath string    custom file path to save the exported app state JSON
      --exportStatsPath string    custom file path to save the exported simulation statistics JSON
      --genesis string            custom simulation genesis file; cannot be used with params file
      --genesisTime int           override genesis UNIX time instead of using a random UNIX time
  -h, --help                      help for simulate
      --initialBlockHeight int    initial block to start the simulation (default 1)
      --lean                      lean simulation log output
      --numBlocks int             number of new blocks to simulate from the initial block height (default 200)
      --params string             custom simulation params file which overrides any random params; cannot be used with genesis
      --period uint               run slow invariants only once every period assertions
      --printAllInvariants        print all invariants if a broken invariant is found
      --seed int                  simulation random seed (default 42)
      --simulateEveryOperation    run slow invariants every operation
  -v, --verbose                   verbose log output
```

**SEE ALSO**

* [ignite chain](#ignite-chain)	 - Build, initialize and start a blockchain node or perform other actions on the blockchain


## ignite completion

Generate the autocompletion script for the specified shell

**Synopsis**

Generate the autocompletion script for ignite for the specified shell.
See each sub-command's help for details on how to use the generated script.


**Options**

```
  -h, --help   help for completion
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite completion bash](#ignite-completion-bash)	 - Generate the autocompletion script for bash
* [ignite completion fish](#ignite-completion-fish)	 - Generate the autocompletion script for fish
* [ignite completion powershell](#ignite-completion-powershell)	 - Generate the autocompletion script for powershell
* [ignite completion zsh](#ignite-completion-zsh)	 - Generate the autocompletion script for zsh


## ignite completion bash

Generate the autocompletion script for bash

**Synopsis**

Generate the autocompletion script for the bash shell.

This script depends on the 'bash-completion' package.
If it is not installed already, you can install it via your OS's package manager.

To load completions in your current shell session:

	source <(ignite completion bash)

To load completions for every new session, execute once:

**#### Linux:**

	ignite completion bash > /etc/bash_completion.d/ignite

**#### macOS:**

	ignite completion bash > $(brew --prefix)/etc/bash_completion.d/ignite

You will need to start a new shell for this setup to take effect.


```
ignite completion bash
```

**Options**

```
  -h, --help              help for bash
      --no-descriptions   disable completion descriptions
```

**SEE ALSO**

* [ignite completion](#ignite-completion)	 - Generate the autocompletion script for the specified shell


## ignite completion fish

Generate the autocompletion script for fish

**Synopsis**

Generate the autocompletion script for the fish shell.

To load completions in your current shell session:

	ignite completion fish | source

To load completions for every new session, execute once:

	ignite completion fish > ~/.config/fish/completions/ignite.fish

You will need to start a new shell for this setup to take effect.


```
ignite completion fish [flags]
```

**Options**

```
  -h, --help              help for fish
      --no-descriptions   disable completion descriptions
```

**SEE ALSO**

* [ignite completion](#ignite-completion)	 - Generate the autocompletion script for the specified shell


## ignite completion powershell

Generate the autocompletion script for powershell

**Synopsis**

Generate the autocompletion script for powershell.

To load completions in your current shell session:

	ignite completion powershell | Out-String | Invoke-Expression

To load completions for every new session, add the output of the above command
to your powershell profile.


```
ignite completion powershell [flags]
```

**Options**

```
  -h, --help              help for powershell
      --no-descriptions   disable completion descriptions
```

**SEE ALSO**

* [ignite completion](#ignite-completion)	 - Generate the autocompletion script for the specified shell


## ignite completion zsh

Generate the autocompletion script for zsh

**Synopsis**

Generate the autocompletion script for the zsh shell.

If shell completion is not already enabled in your environment you will need
to enable it.  You can execute the following once:

	echo "autoload -U compinit; compinit" >> ~/.zshrc

To load completions in your current shell session:

	source <(ignite completion zsh); compdef _ignite ignite

To load completions for every new session, execute once:

**#### Linux:**

	ignite completion zsh > "${fpath[1]}/_ignite"

**#### macOS:**

	ignite completion zsh > $(brew --prefix)/share/zsh/site-functions/_ignite

You will need to start a new shell for this setup to take effect.


```
ignite completion zsh [flags]
```

**Options**

```
  -h, --help              help for zsh
      --no-descriptions   disable completion descriptions
```

**SEE ALSO**

* [ignite completion](#ignite-completion)	 - Generate the autocompletion script for the specified shell


## ignite docs

Show Ignite CLI docs

```
ignite docs [flags]
```

**Options**

```
  -h, --help   help for docs
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain


## ignite generate

Generate clients, API docs from source code

**Synopsis**

Generate clients, API docs from source code.

Such as compiling protocol buffer files into Go or implement particular functionality, for example, generating an OpenAPI spec.

Produced source code can be regenerated by running a command again and is not meant to be edited by hand.

**Options**

```
      --clear-cache   clear the build cache (advanced)
  -h, --help          help for generate
  -p, --path string   path of the app (default ".")
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite generate dart](#ignite-generate-dart)	 - Generate a Dart client
* [ignite generate openapi](#ignite-generate-openapi)	 - Generate generates an OpenAPI spec for your chain from your config.yml
* [ignite generate proto-go](#ignite-generate-proto-go)	 - Generate proto based Go code needed for the app's source code
* [ignite generate vuex](#ignite-generate-vuex)	 - Generate Vuex store for you chain's frontend from your config.yml


## ignite generate dart

Generate a Dart client

```
ignite generate dart [flags]
```

**Options**

```
  -h, --help   help for dart
  -y, --yes    Answers interactive yes/no questions with yes
```

**Options inherited from parent commands**

```
      --clear-cache   clear the build cache (advanced)
  -p, --path string   path of the app (default ".")
```

**SEE ALSO**

* [ignite generate](#ignite-generate)	 - Generate clients, API docs from source code


## ignite generate openapi

Generate generates an OpenAPI spec for your chain from your config.yml

```
ignite generate openapi [flags]
```

**Options**

```
  -h, --help   help for openapi
  -y, --yes    Answers interactive yes/no questions with yes
```

**Options inherited from parent commands**

```
      --clear-cache   clear the build cache (advanced)
  -p, --path string   path of the app (default ".")
```

**SEE ALSO**

* [ignite generate](#ignite-generate)	 - Generate clients, API docs from source code


## ignite generate proto-go

Generate proto based Go code needed for the app's source code

```
ignite generate proto-go [flags]
```

**Options**

```
  -h, --help   help for proto-go
  -y, --yes    Answers interactive yes/no questions with yes
```

**Options inherited from parent commands**

```
      --clear-cache   clear the build cache (advanced)
  -p, --path string   path of the app (default ".")
```

**SEE ALSO**

* [ignite generate](#ignite-generate)	 - Generate clients, API docs from source code


## ignite generate vuex

Generate Vuex store for you chain's frontend from your config.yml

```
ignite generate vuex [flags]
```

**Options**

```
  -h, --help                help for vuex
      --proto-all-modules   enables proto code generation for 3rd party modules used in your chain
  -y, --yes                 Answers interactive yes/no questions with yes
```

**Options inherited from parent commands**

```
      --clear-cache   clear the build cache (advanced)
  -p, --path string   path of the app (default ".")
```

**SEE ALSO**

* [ignite generate](#ignite-generate)	 - Generate clients, API docs from source code


## ignite node

Make calls to a live blockchain node

**Options**

```
  -h, --help          help for node
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite node query](#ignite-node-query)	 - Querying subcommands
* [ignite node tx](#ignite-node-tx)	 - Transactions subcommands


## ignite node query

Querying subcommands

**Options**

```
  -h, --help   help for query
```

**Options inherited from parent commands**

```
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node](#ignite-node)	 - Make calls to a live blockchain node
* [ignite node query bank](#ignite-node-query-bank)	 - Querying commands for the bank module
* [ignite node query tx](#ignite-node-query-tx)	 - Query for transaction by hash


## ignite node query bank

Querying commands for the bank module

**Options**

```
  -h, --help   help for bank
```

**Options inherited from parent commands**

```
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node query](#ignite-node-query)	 - Querying subcommands
* [ignite node query bank balances](#ignite-node-query-bank-balances)	 - Query for account balances by account name or address


## ignite node query bank balances

Query for account balances by account name or address

```
ignite node query bank balances [from_account_or_address] [flags]
```

**Options**

```
      --address-prefix string    Account address prefix (default "cosmos")
      --count-total              count total number of records in all balances to query for
  -h, --help                     help for balances
      --home string              home directory used for blockchains
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
      --limit uint               pagination limit of all balances to query for (default 100)
      --offset uint              pagination offset of all balances to query for
      --page uint                pagination page of all balances to query for. This sets offset to a multiple of limit (default 1)
      --page-key string          pagination page-key of all balances to query for
      --reverse                  results are sorted in descending order
```

**Options inherited from parent commands**

```
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node query bank](#ignite-node-query-bank)	 - Querying commands for the bank module


## ignite node query tx

Query for transaction by hash

```
ignite node query tx [hash] [flags]
```

**Options**

```
  -h, --help   help for tx
```

**Options inherited from parent commands**

```
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node query](#ignite-node-query)	 - Querying subcommands


## ignite node tx

Transactions subcommands

**Options**

```
      --address-prefix string    Account address prefix (default "cosmos")
      --broadcast-mode string    Transaction broadcasting mode (sync|async|block), use sync if you encounter timeouts (default "block")
      --fees string              Fees to pay along with transaction; eg: 10uatom
      --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default "auto")
      --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
      --generate-only            Build an unsigned transaction and write it to STDOUT
  -h, --help                     help for tx
      --home string              home directory used for blockchains
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**Options inherited from parent commands**

```
      --node string   <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node](#ignite-node)	 - Make calls to a live blockchain node
* [ignite node tx bank](#ignite-node-tx-bank)	 - Bank transaction subcommands


## ignite node tx bank

Bank transaction subcommands

**Options**

```
  -h, --help   help for bank
```

**Options inherited from parent commands**

```
      --address-prefix string    Account address prefix (default "cosmos")
      --broadcast-mode string    Transaction broadcasting mode (sync|async|block), use sync if you encounter timeouts (default "block")
      --fees string              Fees to pay along with transaction; eg: 10uatom
      --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default "auto")
      --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
      --generate-only            Build an unsigned transaction and write it to STDOUT
      --home string              home directory used for blockchains
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
      --node string              <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node tx](#ignite-node-tx)	 - Transactions subcommands
* [ignite node tx bank send](#ignite-node-tx-bank-send)	 - Send funds from one account to another.


## ignite node tx bank send

Send funds from one account to another.

```
ignite node tx bank send [from_account_or_address] [to_account_or_address] [amount] [flags]
```

**Options**

```
  -h, --help   help for send
```

**Options inherited from parent commands**

```
      --address-prefix string    Account address prefix (default "cosmos")
      --broadcast-mode string    Transaction broadcasting mode (sync|async|block), use sync if you encounter timeouts (default "block")
      --fees string              Fees to pay along with transaction; eg: 10uatom
      --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default "auto")
      --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
      --generate-only            Build an unsigned transaction and write it to STDOUT
      --home string              home directory used for blockchains
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
      --node string              <host>:<port> to tendermint rpc interface for this chain (default "https://rpc.cosmos.network:443")
```

**SEE ALSO**

* [ignite node tx bank](#ignite-node-tx-bank)	 - Bank transaction subcommands


## ignite relayer

Connect blockchains by using IBC protocol

**Options**

```
  -h, --help   help for relayer
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite relayer configure](#ignite-relayer-configure)	 - Configure source and target chains for relaying
* [ignite relayer connect](#ignite-relayer-connect)	 - Link chains associated with paths and start relaying tx packets in between


## ignite relayer configure

Configure source and target chains for relaying

```
ignite relayer configure [flags]
```

**Options**

```
  -a, --advanced                  Advanced configuration options for custom IBC modules
  -h, --help                      help for configure
      --keyring-backend string    Keyring backend to store your account keys (default "test")
      --keyring-dir string        The accounts keyring directory (default "/home/runner/.ignite/accounts")
      --ordered                   Set the channel as ordered
  -r, --reset                     Reset the relayer config
      --source-account string     Source Account
      --source-client-id string   use a custom client id for source
      --source-faucet string      Faucet address of the source chain
      --source-gaslimit int       Gas limit used for transactions on source chain
      --source-gasprice string    Gas price used for transactions on source chain
      --source-port string        IBC port ID on the source chain
      --source-prefix string      Address prefix of the source chain
      --source-rpc string         RPC address of the source chain
      --source-version string     Module version on the source chain
      --target-account string     Target Account
      --target-client-id string   use a custom client id for target
      --target-faucet string      Faucet address of the target chain
      --target-gaslimit int       Gas limit used for transactions on target chain
      --target-gasprice string    Gas price used for transactions on target chain
      --target-port string        IBC port ID on the target chain
      --target-prefix string      Address prefix of the target chain
      --target-rpc string         RPC address of the target chain
      --target-version string     Module version on the target chain
```

**SEE ALSO**

* [ignite relayer](#ignite-relayer)	 - Connect blockchains by using IBC protocol


## ignite relayer connect

Link chains associated with paths and start relaying tx packets in between

```
ignite relayer connect [<path>,...] [flags]
```

**Options**

```
  -h, --help                     help for connect
      --keyring-backend string   Keyring backend to store your account keys (default "test")
      --keyring-dir string       The accounts keyring directory (default "/home/runner/.ignite/accounts")
```

**SEE ALSO**

* [ignite relayer](#ignite-relayer)	 - Connect blockchains by using IBC protocol


## ignite scaffold

Scaffold a new blockchain, module, message, query, and more

**Synopsis**

Scaffolding is a quick way to generate code for major pieces of your
application.

For details on each scaffolding target (chain, module, message, etc.) run the
corresponding command with a "--help" flag, for example, "ignite scaffold chain
--help".

The Ignite team strongly recommends committing the code to a version control
system before running scaffolding commands. This will make it easier to see the
changes to the source code as well as undo the command if you've decided to roll
back the changes.

This blockchain you create with the chain scaffolding command uses the modular
Cosmos SDK framework and imports many standard modules for functionality like
proof of stake, token transfer, inter-blockchain connectivity, governance, and
more. Custom functionality is implemented in modules located by convention in
the "x/" directory. By default, your blockchain comes with an empty custom
module. Use the module scaffolding command to create an additional module.

An empty custom module doesn't do much, it's basically a container for logic
that is responsible for processing transactions and changing the application
state. Cosmos SDK blockchains work by processing user-submitted signed
transactions, which contain one or more messages. A message contains data that
describes a state transition. A module can be responsible for handling any
number of messages.

A message scaffolding command will generate the code for handling a new type of
Cosmos SDK message. Message fields describe the state transition that the
message is intended to produce if processed without errors.

Scaffolding messages is useful to create individual "actions" that your module
can perform. Sometimes, however, you want your blockchain to have the
functionality to create, read, update and delete (CRUD) instances of a
particular type. Depending on how you want to store the data there are three
commands that scaffold CRUD functionality for a type: list, map, and single.
These commands create four messages (one for each CRUD action), and the logic to
add, delete, and fetch the data from the store. If you want to scaffold only the
logic, for example, you've decided to scaffold messages separately, you can do
that as well with the "--no-message" flag.

Reading data from a blockchain happens with a help of queries. Similar to how
you can scaffold messages to write data, you can scaffold queries to read the
data back from your blockchain application.

You can also scaffold a type, which just produces a new protocol buffer file
with a proto message description. Note that proto messages produce (and
correspond with) Go types whereas Cosmos SDK messages correspond to proto "rpc"
in the "Msg" service.

If you're building an application with custom IBC logic, you might need to
scaffold IBC packets. An IBC packet represents the data sent from one blockchain
to another. You can only scaffold IBC packets in IBC-enabled modules scaffolded
with an "--ibc" flag. Note that the default module is not IBC-enabled.


**Options**

```
  -h, --help   help for scaffold
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite scaffold band](#ignite-scaffold-band)	 - Scaffold an IBC BandChain query oracle to request real-time data
* [ignite scaffold chain](#ignite-scaffold-chain)	 - Fully-featured Cosmos SDK blockchain
* [ignite scaffold flutter](#ignite-scaffold-flutter)	 - A Flutter app for your chain
* [ignite scaffold list](#ignite-scaffold-list)	 - CRUD for data stored as an array
* [ignite scaffold map](#ignite-scaffold-map)	 - CRUD for data stored as key-value pairs
* [ignite scaffold message](#ignite-scaffold-message)	 - Message to perform state transition on the blockchain
* [ignite scaffold module](#ignite-scaffold-module)	 - Scaffold a Cosmos SDK module
* [ignite scaffold packet](#ignite-scaffold-packet)	 - Message for sending an IBC packet
* [ignite scaffold query](#ignite-scaffold-query)	 - Query to get data from the blockchain
* [ignite scaffold single](#ignite-scaffold-single)	 - CRUD for data stored in a single location
* [ignite scaffold type](#ignite-scaffold-type)	 - Scaffold only a type definition
* [ignite scaffold vue](#ignite-scaffold-vue)	 - Vue 3 web app template


## ignite scaffold band

Scaffold an IBC BandChain query oracle to request real-time data

**Synopsis**

Scaffold an IBC BandChain query oracle to request real-time data from BandChain scripts in a specific IBC-enabled Cosmos SDK module

```
ignite scaffold band [queryName] --module [moduleName] [flags]
```

**Options**

```
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for band
      --module string   IBC Module to add the packet into
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold chain

Fully-featured Cosmos SDK blockchain

**Synopsis**

Create a new application-specific Cosmos SDK blockchain.

For example, the following command will create a blockchain called "hello" in
the "hello/" directory:

  ignite scaffold chain hello

A project name can be a simple name or a URL. The name will be used as the Go
module path for the project. Examples of project names:

  ignite scaffold chain foo
  ignite scaffold chain foo/bar
  ignite scaffold chain example.org/foo
  ignite scaffold chain github.com/username/foo
		
A new directory with source code files will be created in the current directory.
To use a different path use the "--path" flag.

Most of the logic of your blockchain is written in custom modules. Each module
effectively encapsulates an independent piece of functionality. Following the
Cosmos SDK convention, custom modules are stored inside the "x/" directory. By
default, Ignite creates a module with a name that matches the name of the
project. To create a blockchain without a default module use the "--no-module"
flag. Additional modules can be added after a project is created with "ignite
scaffold module" command.

Account addresses on Cosmos SDK-based blockchains have string prefixes. For
example, the Cosmos Hub blockchain uses the default "cosmos" prefix, so that
addresses look like this: "cosmos12fjzdtqfrrve7zyg9sv8j25azw2ua6tvu07ypf". To
use a custom address prefix use the "--address-prefix" flag. For example:

  ignite scaffold chain foo --address-prefix bar

By default when compiling a blockchain's source code Ignite creates a cache to
speed up the build process. To clear the cache when building a blockchain use
the "--clear-cache" flag. It is very unlikely you will ever need to use this
flag.

The blockchain is using the Cosmos SDK modular blockchain framework. Learn more
about Cosmos SDK on https://docs.cosmos.network


```
ignite scaffold chain [name] [flags]
```

**Options**

```
      --address-prefix string   Account address prefix (default "cosmos")
      --clear-cache             clear the build cache (advanced)
  -h, --help                    help for chain
      --no-module               Create a project without a default module
  -p, --path string             Create a project in a specific path (default ".")
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold flutter

A Flutter app for your chain

```
ignite scaffold flutter [flags]
```

**Options**

```
  -h, --help          help for flutter
  -p, --path string   path to scaffold content of the Flutter app (default "./flutter")
  -y, --yes           Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold list

CRUD for data stored as an array

```
ignite scaffold list NAME [field]... [flags]
```

**Options**

```
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for list
      --module string   Module to add into. Default is app's main module
      --no-message      Disable CRUD interaction messages scaffolding
      --no-simulation   Disable CRUD simulation scaffolding
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold map

CRUD for data stored as key-value pairs

```
ignite scaffold map NAME [field]... [flags]
```

**Options**

```
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for map
      --index strings   fields that index the value (default [index])
      --module string   Module to add into. Default is app's main module
      --no-message      Disable CRUD interaction messages scaffolding
      --no-simulation   Disable CRUD simulation scaffolding
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold message

Message to perform state transition on the blockchain

```
ignite scaffold message [name] [field1] [field2] ... [flags]
```

**Options**

```
      --clear-cache        clear the build cache (advanced)
  -d, --desc string        Description of the command
  -h, --help               help for message
      --module string      Module to add the message into. Default: app's main module
      --no-simulation      Disable CRUD simulation scaffolding
  -p, --path string        path of the app (default ".")
  -r, --response strings   Response fields
      --signer string      Label for the message signer (default: creator)
  -y, --yes                Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold module

Scaffold a Cosmos SDK module

**Synopsis**

Scaffold a new Cosmos SDK module.

Cosmos SDK is a modular framework and each independent piece of functionality is
implemented in a separate module. By default your blockchain imports a set of
standard Cosmos SDK modules. To implement custom functionality of your
blockchain, scaffold a module and implement the logic of your application.

This command does the following:

* Creates a directory with module's protocol buffer files in "proto/"
* Creates a directory with module's boilerplate Go code in "x/"
* Imports the newly created module by modifying "app/app.go"
* Creates a file in "testutil/keeper/" that contains logic to create a keeper
  for testing purposes

This command will proceed with module scaffolding even if "app/app.go" doesn't
have the required default placeholders. If the placeholders are missing, you
will need to modify "app/app.go" manually to import the module. If you want the
command to fail if it can't import the module, use the "--require-registration"
flag.

To scaffold an IBC-enabled module use the "--ibc" flag. An IBC-enabled module is
like a regular module with the addition of IBC-specific logic and placeholders
to scaffold IBC packets with "ignite scaffold packet".

A module can depend on one or more other modules and import their keeper
methods. To scaffold a module with a dependency use the "--dep" flag

For example, your new custom module "foo" might have functionality that requires
sending tokens between accounts. The method for sending tokens is a defined in
the "bank"'s module keeper. You can scaffold a "foo" module with the dependency
on "bank" with the following command:

  ignite scaffold module foo --dep bank

You can then define which methods you want to import from the "bank" keeper in
"expected_keepers.go".

You can also scaffold a module with a list of dependencies that can include both
standard and custom modules (provided they exist):

  ignite scaffold module bar --dep foo,mint,account

Note: the "--dep" flag doesn't install third-party modules into your
application, it just generates extra code that specifies which existing modules
your new custom module depends on.

A Cosmos SDK module can have parameters (or "params"). Params are values that
can be set at the genesis of the blockchain and can be modified while the
blockchain is running. An example of a param is "Inflation rate change" of the
"mint" module. A module can be scaffolded with params using the "--params" flag
that accepts a list of param names. By default params are of type "string", but
you can specify a type for each param. For example:

  ignite scaffold module foo --params baz:uint,bar:bool

Refer to Cosmos SDK documentation to learn more about modules, dependencies and
params.


```
ignite scaffold module [name] [flags]
```

**Options**

```
      --clear-cache            clear the build cache (advanced)
      --dep strings            module dependencies (e.g. --dep account,bank)
  -h, --help                   help for module
      --ibc                    scaffold an IBC module
      --ordering string        channel ordering of the IBC module [none|ordered|unordered] (default "none")
      --params strings         scaffold module params
  -p, --path string            path of the app (default ".")
      --require-registration   if true command will fail if module can't be registered
  -y, --yes                    Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold packet

Message for sending an IBC packet

**Synopsis**

Scaffold an IBC packet in a specific IBC-enabled Cosmos SDK module

```
ignite scaffold packet [packetName] [field1] [field2] ... --module [moduleName] [flags]
```

**Options**

```
      --ack strings     Custom acknowledgment type (field1,field2,...)
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for packet
      --module string   IBC Module to add the packet into
      --no-message      Disable send message scaffolding
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold query

Query to get data from the blockchain

```
ignite scaffold query [name] [request_field1] [request_field2] ... [flags]
```

**Options**

```
      --clear-cache        clear the build cache (advanced)
  -d, --desc string        Description of the command
  -h, --help               help for query
      --module string      Module to add the query into. Default: app's main module
      --paginated          Define if the request can be paginated
  -p, --path string        path of the app (default ".")
  -r, --response strings   Response fields
  -y, --yes                Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold single

CRUD for data stored in a single location

```
ignite scaffold single NAME [field]... [flags]
```

**Options**

```
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for single
      --module string   Module to add into. Default is app's main module
      --no-message      Disable CRUD interaction messages scaffolding
      --no-simulation   Disable CRUD simulation scaffolding
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold type

Scaffold only a type definition

```
ignite scaffold type NAME [field]... [flags]
```

**Options**

```
      --clear-cache     clear the build cache (advanced)
  -h, --help            help for type
      --module string   Module to add into. Default is app's main module
      --no-message      Disable CRUD interaction messages scaffolding
      --no-simulation   Disable CRUD simulation scaffolding
  -p, --path string     path of the app (default ".")
      --signer string   Label for the message signer (default: creator)
  -y, --yes             Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite scaffold vue

Vue 3 web app template

```
ignite scaffold vue [flags]
```

**Options**

```
  -h, --help          help for vue
  -p, --path string   path to scaffold content of the Vue.js app (default "./vue")
  -y, --yes           Answers interactive yes/no questions with yes
```

**SEE ALSO**

* [ignite scaffold](#ignite-scaffold)	 - Scaffold a new blockchain, module, message, query, and more


## ignite tools

Tools for advanced users

**Options**

```
  -h, --help   help for tools
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain
* [ignite tools ibc-relayer](#ignite-tools-ibc-relayer)	 - Typescript implementation of an IBC relayer
* [ignite tools ibc-setup](#ignite-tools-ibc-setup)	 - Collection of commands to quickly setup a relayer
* [ignite tools protoc](#ignite-tools-protoc)	 - Execute the protoc command


## ignite tools ibc-relayer

Typescript implementation of an IBC relayer

```
ignite tools ibc-relayer [--] [...] [flags]
```

**Examples**

```
ignite tools ibc-relayer -- -h
```

**Options**

```
  -h, --help   help for ibc-relayer
```

**SEE ALSO**

* [ignite tools](#ignite-tools)	 - Tools for advanced users


## ignite tools ibc-setup

Collection of commands to quickly setup a relayer

```
ignite tools ibc-setup [--] [...] [flags]
```

**Examples**

```
ignite tools ibc-setup -- -h
ignite tools ibc-setup -- init --src relayer_test_1 --dest relayer_test_2
```

**Options**

```
  -h, --help   help for ibc-setup
```

**SEE ALSO**

* [ignite tools](#ignite-tools)	 - Tools for advanced users


## ignite tools protoc

Execute the protoc command

**Synopsis**

The protoc command. You don't need to setup the global protoc include folder with -I, it's automatically handled

```
ignite tools protoc [--] [...] [flags]
```

**Examples**

```
ignite tools protoc -- --version
```

**Options**

```
  -h, --help   help for protoc
```

**SEE ALSO**

* [ignite tools](#ignite-tools)	 - Tools for advanced users


## ignite version

Print the current build information

```
ignite version [flags]
```

**Options**

```
  -h, --help   help for version
```

**SEE ALSO**

* [ignite](#ignite)	 - Ignite CLI offers everything you need to scaffold, test, build, and launch your blockchain

