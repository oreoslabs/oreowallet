<p align="center">
  <img src="assets/logo.svg" width="80" alt="Logo for OreoWallet" />
</p>

<h1 align="center">
  OreoWallet
</h1>

<p align="center">
  A browser extension wallet for IronFish blockchain.
</p>

<div align="center">

[![Twitter Follow](https://img.shields.io/twitter/follow/oreowallet?style=social)](https://twitter.com/oreowallet)

</div>

## Intro

There are 4 types wallet for privacy blockchain like IronFish on my side.

- Type1: Cex wallet, fully-custodial wallet.
- Type2: PrivateKey is safely saved locally while viewkey is uploaded to a backend server for better experience. Transactions are signed locally while transaction decryption and utxos-indexing rely on customsized remote server.
- Type3: Both transaction decryption and creation are performed locally while transaction fetching/broadcasting rely on a public remote rpc like metamask.
- Type4: A wallet embedded with a full node, syncs blocks/transactions with P2P network directly.

OreoWallet aims to build both Type2 and Type3 wallet for IronFish blockchain. Currently, we are on the way to Type2 wallet.

## Documentation

There is a README in each package, as well as comments in the source code.

## Project structure

<pre>
oreowallet
├── <a href="https://github.com/oreoslabs/oreowallet-extension">oreowallet-extension</a>: OreoWallet frontend ui 
├── <a href="https://github.com/oreoslabs/ironfish-optimize">ironfish-optimize</a>: Optimized version of ironfish-rust for wasm env
├── <a href="https://github.com/oreoslabs/ironfish-wasm">ironfish-wasm</a>: Core wasm sdk of OreoWallet
├── <a href="https://github.com/oreoslabs/ironfish-server">server</a>: Backend for necessary api service and task scheduling
├── <a href="https://github.com/oreoslabs/ironfish-server">prover</a>: Prover to genereate proof for OreoWallet transactions
</pre>

## OreoWallet V1 arch (Type2)

![basic arch](assets/arch.svg)


## Issues

If you find a bug or have a feature request, please [open an issue](https://github.com/oreoslabs/oreowallet/issues/new).

## Contributing

Check out [CONTRIBUTING.md](./CONTRIBUTING.md) for details on how to contribute.

## Get help

Reach out to the community on [Twitter](https://twitter.com/oreowallet) to get help.

