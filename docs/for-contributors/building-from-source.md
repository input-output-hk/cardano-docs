# Building Cardano SL and Daedalus from Source

[//]: # (<2017-01-15>)

Cardano SL consists of a collection of binaries that constitutes
backend, a PureScript API for the Electron-based wallet and the
Electron-based wallet called “Daedalus”. You can read more about design
and architecture of Cardano SL in the [Implementation
Guide](/for-contributors/implementation.md).

## Cardano SL and Daedalus Bridge

Source code for both Cardano SL and Daedalus Bridge can be obtained
(here)[https://github.com/input-output-hk/pos-haskell-prototype]

We strongly suggest using [Nix package
manager](https://nixos.org/nix/download.html) to get the right
dependencies for building Cardano SL. It will fetch the correct
`openssl` version, but won't override system-installed version, same
goes for dependencies such as `rocksdb` with which many developers
reported having problems. The rest of documentation assumes that you
have Nix package manager installed on your machine.

To build the project, clone the source base and navigate to the root
directory of it:

```
git clone https://github.com/input-output-hk/pos-haskell-prototype.git
cd pos-haskell-prototype
```

Then enter `nix-shell` and if you build a project written in Haskell
language for the first time on this machine, run `stack setup`.

```
Tue Jan 10 sweater@chill ~/github/pos-haskell-prototype (master) 
λ nix-shell
[nix-shell:~/github/pos-haskell-prototype]$ stack setup
* snip *
```

After we have obtained relevant Haskell compiler version, let's enable
Nix for all `stack` builds. To do so, make sure that your
`~/.stack/config.yaml` has the following option:

```
nix:
  enable: true
```

Now in order to build Cardano SL with wallet capabilities, run the
following command:

```
[nix-shell:~/github/pos-haskell-prototype]
$ stack build --flag cardano-sl:with-wallet --flag cardano-sl:with-web
```

Here is [asciinema
cast](http://asciinema.org/a/47vbdch8srbhf3j5kta7j9bov) of the project building.

We suggest having at least 8GB of RAM and some swap space for the build
process. As the project is fairly large and GHC parallelizes builds very
effectively, memory and CPU consumption during the build process is
demanding.

After the project is built, you'll be able to launch built binaries
using `stack exec` command. Let's discuss important binaries briefly
before proceeding to next steps.

### cardano-node

Binary `cardano-node` is the most important binary of the system. It
launches nodes. In order to attach to a network, we have to supply it
with Hardened Kadmelia DHT peer information. Peer discovery will follow
if initial DHT peer is available. The syntax for communicating initial
DHT peer is the following: `--peer HOST:PORT/HOST_ID`, for example
`discover.memorici.de:21989/MHdtsP-oPf7UWly7QuXnLK5RDB8=`.

[//]: # (TODO: Actually put a small dev-only net with a discoverable)
[//]: # (peers which will send a recruitment propsal message to people)
[//]: # (who bothered to build the system from scratch in the early days)
[//]: # (of testnet release)

Before providing an example of running the node, let's briefly discuss
the trickiest command line arguments.

When we bootstrap a testnet, we distribute stake across several
addresses in genesis block. The distributions that we support are flat
distribution and Bitcoin distribution. Spending and VSS keys are
generated for genesis block, if a node has access to a genesis key
mapping, we can provide the index of the secret key in this mapping
using `--vss-genesis N` and `--spending-genesis N`, where `N` is index
in this mapping.

Example of a local invoaction connecting to HostID
`MHdtsP-oPf7UWly007QuXnLK5RD=`:

```
stack exec cardano-node -- \
  --port 3002 \
  --db-path run/node-db2 \
  --vss-genesis 2 --spending-genesis 2 \
  --peer 127.0.0.1:3000/MHdtsP-oPf7UWly007QuXnLK5RD= \
  --json-log=logs/2017-01-10_035413/node2.json \
  --logs-prefix logs/2017-01-10_035413 \
  --log-config logs/2017-01-10_035413/conf/node2.log.yaml \
  --flat-distr "(3, 100000)"
```

### cardano-smart-gen

_Pending_
