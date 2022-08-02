# meteor-test
> This is the updated Meteor Testnet on Comdex

> GENESIS PUBLISHED

> PEERS PUBLISHED

2nd testnet for comdex-official/comdex application.

## Hardware Requirements
* **Minimal**
    * 4 GB RAM
    * 100 GB SSD
    * 3.2 x4 GHz CPU
* **Recommended**
    * 8 GB RAM
    * 100 GB NVME SSD
    * 4.2 GHz x6 CPU

## Operating System
* Linux/Windows/MacOS(x86)
* **Recommended**
    * Linux(x86_64)

## Installation Steps
>Prerequisite: go1.18+ required. [ref](https://golang.org/doc/install)

   Append the below lines to the file ${HOME}/.bashrc and execute the command source ${HOME}/.bashrc to reflect in the current Terminal session
   ```shell
   export GOROOT=/usr/lib/go
   export GOPATH=${HOME}/go
   export GOBIN=${GOPATH}/bin
   export PATH=${PATH}:${GOROOT}/bin:${GOBIN}
   ```

>Prerequisite: git. [ref](https://github.com/git/git)

>Optional requirement: GNU make. [ref](https://www.gnu.org/software/make/manual/html_node/index.html)

* Clone git repository
```shell
git clone https://github.com/comdex-official/comdex.git
```
* Checkout latest tag
```shell
cd comdex
git fetch --tags
git checkout v2.1.0
```
* Install
```shell
make all
```

### Generate keys

`comdex keys add [key_name]`

or

`comdex keys add [key_name] --recover` to regenerate keys with your [BIP39](https://github.com/bitcoin/bips/tree/master/bip-0039) mnemonic


## Validator setup instructions

### Running a full node

* [Install](#installation-steps) comdex core application
* Initialize node
```shell
comdex init {{NODE_NAME}} --chain-id meteor-test
```
* Download the latest genesis and replace it
```shell
cd ${HOME}/.comdex/config
rm genesis.json
wget https://raw.githubusercontent.com/comdex-official/networks/main/testnet/meteor-test/genesis.json
```
* Verify the genesis hash (the following command should match ```b0744029560d65bd5d81dbe055704708a33c3d51594b02ea575cf4b56d7f506e```
```shell
sha256 genesis.json
```
* Update the existing peers in ```${HOME}/.comdex/config/config.toml```
```
persistent_peers = "4202b41ccc3032011969005a215e1dbe36e3ba23@3.109.138.42:26656,223d534f0fd1daeea3578346ad3e49d9cec973b6@54.204.207.38:26656,efa67d2456e8e22e9b29bd127ed3024cffc7ede1@46.166.163.37:26656,494af55997cbb1df62cff1ed4f35b58c31277f63@46.166.172.230:26656"
```
* Restore the snapshot provided by the Comdex Team
```
cd ${HOME}/.comdex/
wget https://binaries-comdex.s3.ap-south-1.amazonaws.com/data.tar.lz4
lz4 -d data.tar.lz4 | tar xf -
```
* Start comdex by running below command or create a `systemd` service to run comdex in background.
```shell
comdex start
```


### Become a validator

* Follow the above steps to run a full node

* Start comdex by running below command or create a `systemd` service to run comdex in background.
```shell
comdex start
```
* Acquire $ucmdx by sending a message to the validators channel in [Discord](https://discord.gg/gH6RTrnexk).
* Run `comdex tendermint show-validator` and copy your consensus public key.
* Send a create-validator transaction
```
comdex tx staking create-validator \
  --amount={{STAKING_AMOUNT}} \
  --pubkey=$(comdex tendermint show-validator) \
  --moniker="anurag.validator.test" \
  --chain-id=meteor-test \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="9000000" \
  --gas="auto" \
  --fees 40000ucmdx \
  --from={{KEY_NAME}}
```

## Version
This chain is currently running on Comdex [v2.1.0](https://github.com/comdex-official/comdex/releases/tag/v2.1.0)
Commit Hash: a2d03e037491dc2779eafebfac1eb4dd14eaa24c
>Note: If your node is running on an older version of the application, please update it to this version at the earliest to avoid being exposed to security vulnerabilities /defects.

## Binary
The binary can be downloaded from [here](https://github.com/comdex-official/comdex/releases/tag/v2.1.0).

## Explorer
The explorer for this chain is hosted [TestNet Explorer](https://meteor-test.comdex.one/)
