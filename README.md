# Hi there 👋!

This is a list of ideas for [the ChainLink Spring hackathon 2022](https://chain.link/hackathon).

## Table of Contents

TODO

## Polkadot

TODO

## Substrate and FRAME

TODO

## Smart Contracts (ink! and `pallet-contracts`)

Some general notes:
* We have comprehensive documentation on ink! and an FAQ at the [ink! documentation portal](https://paritytech.github.io/ink-docs).
* You can find a beginners workshop for ink! [here](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/).
* For deploying and testing ink! contracts locally you can use our `substrate-contrats-node`. See our documentation [here](https://paritytech.github.io/ink-docs/getting-started/running-substrate) on how to run it.

Feel free to ask us any questions that might come up in the [Substrate StackExchange](https://substrate.stackexchange.com/)!


### Idea 1: Enable writing smart contracts for Substrate's `pallet-contracts` in a new language.

Substrate's module for smart contracts, the [`pallet-contracts`](https://github.com/paritytech/substrate/tree/master/frame/contracts), exposes an API to Wasm blobs. This means you can use any language that compiles down to Wasm, which implements this API (or at least parts of it), to write smart contracts for Substrate's `pallet-contracts`.

At the moment there are three languages which do that:

* [Parity's ink!](https://github.com/paritytech/ink) for Rust
* [ask!](https://github.com/patractlabs/ask) for Assembly Script
* The [Solang](https://github.com/hyperledger-labs/solang) compiler for Solidity

You have different options in which you could go for this milestone: 

#### Milestone 1: Write a framework or library for a language that compiles to WebAssembly.

One of the reasons we chose Rust for Parity's ink! was that WebAssembly is a supported target of the Rust compiler. Nowadays there are way more languages that can be compiled to WebAssembly though.

To complete this milestone we expect:
* Implementation of the `pallet-contracts` API for `deploy`, `call`, `seal_input`, and `seal_return`. __(@Alex: Is anything else needed for flipper?)__
* Implementation of the [ink! flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper) (ink!'s hello-world) in the language you chose.
* You can use the metadata file from [here](TODO-INSERT-LINK) to deploy and interact with your contract. There are two browser user interfaces: the [Contracts UI](https://paritytech.github.io/contracts-ui/) or [polkadot-js](https://polkadot.js.org/apps/#/).

#### Milestone 2: …?

### Idea 2: Build a Substrate Oracle chain and write an ink! smart contract that utilizes the oracle information.

#### Milestone 1: Build the Oracle chain in Substrate.

To complete this milestone we expect:
* A Substrate standalone chain that uses off-chain workers to submit inherent extrinsics with the result of an HTTP request ‒ e.g. the price of an asset, but feel free to choose whatever you like.

#### Milestone 2: Write an ink! smart contract which accesses the Oracle results.

To complete this milestone we expect:
* Implement a chain extension for the `pallet-contracts` which makes the oracle information accessible. You can see [this example for how to build a chain extension](https://github.com/paritytech/ink/tree/master/examples/rand-extension)for how this can be done. We also have documentation on the concept of chain extensions [here](https://paritytech.github.io/ink-docs/macros-attributes/chain-extension/). 
* Write an ink! smart contract which calls the chain extension and makes use of the result.

#### Milestone 3: Make your chain parachain-ready.

To complete this milestone we expect:
* Your chain supports running as a parachain.
* It makes the oracle results available to other parachains by implementing XCM. 


### Idea 3: Implement a Dapp user interface for our example contracts.

We have a number of ink! smart contract examples, but so far no user interface targeted at end users.

There are different user interfaces and command-line tools you can use to deploy or interact with contracts:

* [Contracts UI](https://paritytech.github.io/contracts-ui/) (Browser UI)
* [polkadot-js](https://polkadot.js.org/apps/) (Browser UI)
* [cargo-contract](https://github.com/paritytech/cargo-contract) (CLI)

If you are looking for an introduction to the Contracts UI, we can recommend
[ink!'s Guided Tutorial for Beginners](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/).

All those UI's target developers though ‒ they enable deploying and interacting with contracts.

#### Milestone 1: Create a web application for interacting with ink!'s `flipper` example.

The ink! [flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper) is ink!'s hello-world. It's a simple contract and your user interface should allow end users to interact with the contract and display the results of those interactions.

To complete this milestone we expect:
* An interactive web application that allows users to invoke `flip` and `get` and displays the result.

The idea here is that we can use this as a template for developers who want to implement a user interface for their smart contract.

You will have to use the polkadot-js API. TODO link to more info?

Using a hard-coded address of the RPC server is fine.

#### Milestone 2: Create a web application for interacting with ink!'s `multisig` example.

The ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig) is a simple multi signature contract.

To complete this milestone we expect:
* An interactive web application that allows users to execute the `multisig` functions and displays the result.

Using a hard-coded address of the RPC server is fine.

#### Milestone 3: Migrate your web application to use a light client.

So far your web application has used hard-coded addresses of the RPC server which it uses to fetch the results of interacting with a contract.

To be a truly unstoppale Dapp though it has to use a light client and thus no longer relie on a single point of failure RPC node. You can use [`substrate-connect`](https://github.com/paritytech/substrate-connect) to securely connect to the blockchain network without relying on specific 3rd parties.

To complete this milestone we expect:
* Your web application has been migrated to use [`substrate-connect`](https://github.com/paritytech/substrate-connect).


### Idea 4: Implement the SAI stablecoin in ink!.

We would like to see more complex ink! contracts, testing out the boundaries of what is possible.

For this purpose we think implementing the SAI stablecoin in ink! is a great use case. You can find the Solidity SAI implementation [here](https://github.com/makerdao/sai/tree/master/src).
As part of this milestone you would have to port this implementation to ink!.

You don't have to mess around with any external Oracle, just mock the price.

To complete this milestone we expect:
* An implementation of SAI in ink!.
* Your implementation has to contain unit and integration tests so that we can assert that it behaves as advertised.


### Idea 5: Implement a command-line user interface to interact with a smart contract that is deployed to a chain.

We have a command-line interface (CLI) to interact with smart contracts that are deployed on a chain: [`cargo-contract`](https://github.com/paritytech/cargo-contract). Its target audience are developers though and it's a general purpose tool.

What we would like to see is a command-line user interface that enables interacting with one particular contract in a user friendly way.

We think the ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig) provides enough room for building a targeted CLI for users of that contract. You could think about how to abstract things away in your CLI.

To complete this milestone we expect:
* A command-line interface that eases interacting with ink!'s `multisig` example.
* Your tool has to use the [`subxt`](https://github.com/paritytech/subxt/) crate for this purpose. This is the same library used by `cargo-contract` for its `instantiate`, `upload`, and `call` sub-commands (see the [usage notes here](https://github.com/paritytech/cargo-contract#usage)). 
