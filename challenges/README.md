# Chainlink hackathon 2022: Polkadot Challenges 🌈 ☕️

For the Chainlink 2022 hackathon, there are **three main** challenge tracks:

1. The **ink! Smart Contracts Track**: ink! is a Rust-based programming language for writing Web Assembly (Wasm) smart contracts. Developers in the Polkadot and Substrate ecosystem can use ink! to build efficient, high-performance smart contracts and dApps for Wasm virtual machines, which represent an alternative to EVM/Solidity-based smart contract systems. 

2. The **Polkadot Improvement Track**: Work on something that brings your skills together to create a project which will improve the Polkadot ecosystem. From developer tooling to awesome user interfaces, wallets or update existing integrations - the sky's the limit. Let your imagination run wild. Remember, we're paving the way for a multi-chain future, where user experiences are multi-chain and there's the least amount of barriers for developers building in the ecosystem. What comes to mind? This is your chance to tell us. 

3. The **Parachains and Pallets Track**: Dive deep into the Polkadot ecosystem and explore various parachains that are already connected to Polkadot. Build dapps on top of parachains by utilizing the full power of their smart contracting capabilities or by adding logic directly to the runtime. An implementation of an oracle off-chain worker compatible with an ink! smart contract perhaps? Extra points for leveraging Cross Consensus Messaging (XCM) to make full use of one of Polkadot’s biggest features - interoperability. 

Based on the above, here are some of the bounties and prizes we've put together for you. 
You can treat these as guidelines for the type of submissions we'd expect:

|Track | Bounty examples | Prize |
|------|------|--------|
| 1. ink! Smart Contracts Track | [Write ink! Smart contracts for an oracle Substrate chain](#build-a-substrate-oracle-chain-and-write-an-ink-smart-contract-that-utilizes-the-oracle-information) | $5k |
| | [Recreate your favorite dApp in ink!](#implement-the-sai-stablecoin-in-ink) | $10k (2 x $5k) |
| 2. Polkadot Improvement Track | [Make writing Wasm smart contracts more accessible in other languages](#make-writing-wasm-smart-contracts-for-substrate-chains-more-accessible-in-other-languages) | $5k |
| | [Update and integrate the Chainlink <> Polkadot Pallets to a local parachain](#update-and-integrate-the-chainlink--polkadot-pallets-to-a-local-parachain) | $5k |
| | [Create a webapp UI for a pallet or ink! contract of your choice](#implement-a-dapp-ui-for-some-example-ink-contracts) | $5k |
| | [Create an interactive smart contract webapp that uses `substrate-connect`](#make-a-light-client-web-application) | $5k |
| 3. Parachains and pallets track | Best smart contract deployed to a Polkadot Parachain | $5k |
| | Best pallet to integrate to a Polkadot Parachain | $5k |

Below is a more detailed breakdown of the work that each of these exemplar bounties would require (and a little context about why they're exciting to work on!). 👀

### Make writing Wasm smart contracts for Substrate chains more accessible in other languages.

**Track:** Polkadot Improvement Track 

**Prize:** $5k

Substrate's runtime module for smart contracts, the [`pallet-contracts`](https://github.com/paritytech/substrate/tree/master/frame/contracts), exposes an API to Wasm blobs. 
This means you can use any language that compiles down to Wasm, which implements this API (or at least parts of it), to write smart contracts for Substrate's `pallet-contracts`.

At the moment there are three languages which do that:

* [Parity's ink!](https://github.com/paritytech/ink) for Rust.
* [ask!](https://github.com/patractlabs/ask) for Assembly Script.
* The [Solang](https://github.com/hyperledger-labs/solang) compiler for Solidity.

One of the reasons we chose Rust for Parity's ink! was that WebAssembly is a supported target of the Rust compiler. 
Nowadays there are [a lot more languages](https://github.com/appcypher/awesome-wasm-langs) that can be compiled to WebAssembly ...
Wouldn't it be cool to put as many of them to use for smart contract development? 😎

#### Task guidelines

1. Implement the `pallet-contracts` API for `deploy`, `call`, `seal_input`, and `seal_return`.
2. Translate the [ink! flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper) (ink!'s hello-world) to the language you chose.
3. Generate the metadata file for the ink! flipper example.
4. Using the metadata, deploy and interact with your contract using the [Contracts UI](https://paritytech.github.io/contracts-ui/).

### Build a Substrate Oracle chain and write an ink! smart contract that utilizes the oracle information.

**Track:** ink! Smart Contracts Track

**Prize:** $5k

Substrate chains are able to implement "off-chain" workers to fetch information from outside the runtime and submit it it on chain.
Sound familiar? Yes, oracles! Or some off-chain computation job.. 

The gist of it is that you can configure a Substrate chain so that it does the job of fetching off-chain data and passes it into a smart contract. 
You'll need to implement a "chain extension" to do this, i.e. a way for a smart contract to make a call to other runtime modules (called pallets).
Then, get creative with what your smart contract will do with this off-chain data. 

Perhaps your off-chain worker does some computation that your smart contract requires?
What about creating subjective oracles using off-chain workers and ink! smart contracts?
A game maybe?

#### Task guidelines

1. Create a Substrate standalone chain that uses off-chain workers to submit on-chain transactions with the result of an HTTP request, e.g. the price of an asset. Refer to [this guide](https://docs.substrate.io/how-to-guides/v3/ocw/http-requests/) on how to do this.
1. Implement a chain extension for the `pallet-contracts` which makes the oracle information accessible. You can see [this example for how to build a chain extension](https://github.com/paritytech/ink/tree/master/examples/rand-extension) for how this can be done. We also have documentation on the concept of chain extensions [here](https://paritytech.github.io/ink-docs/macros-attributes/chain-extension/). 
1. Write an ink! smart contract which calls the chain extension and makes use of the result in some interesting way.
1. (bonus) Turn your chain into a parachain by following [this guide](https://docs.substrate.io/tutorials/v3/cumulus/polkadot-launch/).
1. (bonus) Make the oracle results available to other parachains by implementing [XCM](https://github.com/paritytech/polkadot/tree/master/xcm) for your chain.


### Implement a Dapp UI for some example ink! contracts.

**Track:** Polkadot Improvement Track

**Prize:** $5k

We have a number of ink! smart contract examples, but so far no user interfaces for end users.

These are some UIs and command-line tools targeted for developers to deploy or interact with contracts:

* [Contracts UI](https://paritytech.github.io/contracts-ui/) (Browser UI)
* [polkadot-js](https://polkadot.js.org/apps/) (Browser UI)
* [cargo-contract](https://github.com/paritytech/cargo-contract) (CLI)

The Contracts UI is a good step in the right direction, however, those UI's aren't really end user friendly...

The idea behind this challenge is to build UIs that can be used as a template for other developers who want to implement a user interface for their smart contract.

You will have to use the [Polkadot-JS API](https://polkadot.js.org/docs/).
Using a hard-coded address of the RPC server is fine.

#### Task guidelines

1. Make UI for the ink! [flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper), ink!'s "hello-world" for smart contracts. 
Your user interface should allow end users to interact with the contract and display the results of those interactions.
1. Make a UI for the ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig), a simple multi-signature contract.
Your UI should be an interactive web application that allows users to execute the `multisig` functions and displays the result.
1. Make a UI for any other ink! contract of your choice.

### Make a light client web application.

**Track:** Polkadot Improvement Track

**Prize:** $5k

Most webapp UIs for smart contract based dApps use an RPC server which to fetch the results of interacting with a contract.
This is also true for most parachain UIs in the Polkadot ecosystem. 

To be a truly unstoppable dApp though, an application should use a light client and thus no longer rely on a single point of failure RPC node. 

Wouldn't it be something to be able to write front-end web apps that spawn their own light clients for their users ... ? 💡🤔

Enter [`substrate-connect`](https://github.com/paritytech/substrate-connect): a javascript library designed to securely connect web apps to their target Substrate blockchain network without relying on 3rd party node provider.

#### Task guidelines

1. Build a web app UI that can interact with a simple ink! contract and uses [`substrate-connect`](https://github.com/paritytech/substrate-connect) to connect to a chain.

or

1. Choose a pallet on an existing chain (e.g. the Democracy pallet or any that interests you) and write a UI web app that uses [`substrate-connect`](https://github.com/paritytech/substrate-connect) to interact with it.
1. (bonus) Give your app the ability to interact with multiple chains.

### Implement the SAI stablecoin in ink!.

We would like to see more complex ink! contracts, testing out the boundaries of what is possible.

For this purpose we think implementing the SAI stablecoin in ink! is a great use case. 
You can find the Solidity SAI implementation [here](https://github.com/makerdao/sai/tree/master/src).
As part of this challenge you would have to port this implementation to ink!.

You don't have to mess around with any external Oracle, just mock the price.

#### Task guidelines 

**Track:** ink! Smart Contracts Track

**Prize:** $5k

1. Implement SAI in ink!
1. Make sure your implementation contains correct units and integration tests so that we can assert that it behaves as advertised.

### Implement a command-line user interface to interact with a smart contract that is deployed to a chain.

**Track:** Polkadot Improvement Track

**Prize:** $5k

We have a command-line interface (CLI) to interact with smart contracts that are deployed on a chain: [`cargo-contract`](https://github.com/paritytech/cargo-contract).
Its target audience are developers though and it's a general purpose tool.

What we would like to see is a command-line user interface that enables interacting with one particular contract in a user friendly way.

We think the ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig) provides enough room for building a targeted CLI for users of that contract. 
You could think about how to abstract things away in your CLI.

#### Task guidelines

1. Write a command-line interface that eases interacting with ink!'s `multisig` example.
1. Make sure your tool uses the [`subxt`](https://github.com/paritytech/subxt/) crate for this purpose. This is the same library used by `cargo-contract` for its `instantiate`, `upload`, and `call` sub-commands (see the [usage notes here](https://github.com/paritytech/cargo-contract#usage)). 

### Update and integrate the Chainlink <> Polkadot Pallets to a local parachain

Want to be the star of this hackathon and create a Substrate chain that can interact with a Chain link node? 🤩

[ insert links etc. ]

Talk to us if you have a project idea and aren't sure whether it fits any of these tracks! 😃