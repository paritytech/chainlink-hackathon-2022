# Hi there 👋

Welcome! 
These are some ideas for things you could build during the [Chainlink 2022 hackathon](https://chain.link/hackathon).
This is by no means an exhaustive list of things.
The intention is that these challenge ideas inspire you to work on prize-winning submissions.

There are three tracks:

1. ink! Smart Contracts Track

    - [Write ink! smart contracts for an oracle Substrate chain](#build-a-substrate-oracle-chain-and-write-an-ink-smart-contract-that-utilizes-the-oracle-information): Winner - $5.000 USD
    - Recreate your favourite dApp in ink!: Top two - $5.000 USD each 

1. Polkadot Improvement Track

    - [Make writing Wasm smart contracts more accessible](#enable-writing-smart-contracts-for-substrates-pallet-contracts-in-a-new-language) in other languages: Winner - $5.000 USD
    - Update and integrate the Chainlink <> Polkadot Pallets to a local parachain: Winner - $5.000 USD
    - [Create a webapp UI for a pallet or an existing ink! smart contract of your choice](#implement-a-dapp-user-interface-for-our-example-contracts): Winner - $5.000 USD
    - [Create an interactive smart contract webapp that uses substrate-connect](#turn-your-webapp-into-a-light-client-application): Winner - $5.000 USD

1. Parachains and Pallets Track
    
    - Best smart contract deployed to a Polkadot Parachain: Winner - $5.000 USD
    - Best pallet to integrate with a Polkadot parachain: Winner - $5.000 USD

## Challenges 🧐

Some general notes:

* Check out the comprehensive documentation on [Substrate](https://docs.substrate.io/v3/getting-started/overview/) and [ink!](https://paritytech.github.io/ink-docs/).
* You can find a beginners workshop for ink! [here](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/).
* For deploying and testing ink! contracts locally you can use our `substrate-contrats-node`. See our documentation [here](https://paritytech.github.io/ink-docs/getting-started/running-substrate) on how to run it.

You can find more resources [here](#resources).

### Enable writing smart contracts for Substrate's `pallet-contracts` in a new language.

Substrate's module for smart contracts, the [`pallet-contracts`](https://github.com/paritytech/substrate/tree/master/frame/contracts), exposes an API to Wasm blobs. This means you can use any language that compiles down to Wasm, which implements this API (or at least parts of it), to write smart contracts for Substrate's `pallet-contracts`.

At the moment there are three languages which do that:

* [Parity's ink!](https://github.com/paritytech/ink) for Rust
* [ask!](https://github.com/patractlabs/ask) for Assembly Script
* The [Solang](https://github.com/hyperledger-labs/solang) compiler for Solidity

One of the reasons we chose Rust for Parity's ink! was that WebAssembly is a supported target of the Rust compiler. Nowadays there are way more languages that can be compiled to WebAssembly though.

To complete this challenge we expect you to:

1. Implement the `pallet-contracts` API for `deploy`, `call`, `seal_input`, and `seal_return`.
2. Translate the [ink! flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper) (ink!'s hello-world) to the language you chose.
3. You can use the metadata file from [here](TODO-INSERT-LINK) to deploy and interact with your contract. There are two browser user interfaces: the [Contracts UI](https://paritytech.github.io/contracts-ui/) or [polkadot-js](https://polkadot.js.org/apps/#/).

### Build a Substrate Oracle chain and write an ink! smart contract that utilizes the oracle information.

You must:
1. Create a Substrate standalone chain that uses off-chain workers to submit inherent extrinsics with the result of an HTTP request ‒ e.g. the price of an asset (feel free to choose whatever you like).
1. Implement a chain extension for the `pallet-contracts` which makes the oracle information accessible. You can see [this example for how to build a chain extension](https://github.com/paritytech/ink/tree/master/examples/rand-extension)for how this can be done. We also have documentation on the concept of chain extensions [here](https://paritytech.github.io/ink-docs/macros-attributes/chain-extension/). 
1. Write an ink! smart contract which calls the chain extension and makes use of the result.
1. Your chain supports running as a parachain.
1. It makes the oracle results available to other parachains by implementing XCM. 


### Implement a Dapp user interface for our example contracts.

We have a number of ink! smart contract examples, but so far no user interface targeted at end users.

There are different user interfaces and command-line tools you can use to deploy or interact with contracts:

* [Contracts UI](https://paritytech.github.io/contracts-ui/) (Browser UI)
* [polkadot-js](https://polkadot.js.org/apps/) (Browser UI)
* [cargo-contract](https://github.com/paritytech/cargo-contract) (CLI)

If you are looking for an introduction to the Contracts UI, we can recommend
[ink!'s Guided Tutorial for Beginners](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/).

All those UI's target developers though ‒ they enable deploying and interacting with contracts.

1. The ink! [flipper example](https://github.com/paritytech/ink/blob/master/examples/flipper) is ink!'s hello-world and a great place to start. 
It's a simple contract and your user interface should allow end users to interact with the contract and display the results of those interactions.

The idea here is that we can use this as a template for developers who want to implement a user interface for their smart contract.

You will have to use the [Polkadot-JS API](https://polkadot.js.org/docs/).
Using a hard-coded address of the RPC server is fine.

1. The ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig) is a simple multi signature contract.

To complete this milestone we expect:
* An interactive web application that allows users to execute the `multisig` functions and displays the result.

Using a hard-coded address of the RPC server is fine.

### Turn your webapp into a light client application.

Most webapp UIs for smart contract based dApps use an RPC server which to fetch the results of interacting with a contract.

To be a truly unstoppable dApp though it has to use a light client and thus no longer rely on a single point of failure RPC node. 
You can use [`substrate-connect`](https://github.com/paritytech/substrate-connect) to securely connect to the blockchain network without relying on specific 3rd parties.

To complete this challenge, build a web app UI that can interact with a simple ink! contract and uses [`substrate-connect`](https://github.com/paritytech/substrate-connect) to connect to a chain.


### Implement the SAI stablecoin in ink!.

We would like to see more complex ink! contracts, testing out the boundaries of what is possible.

For this purpose we think implementing the SAI stablecoin in ink! is a great use case. 
You can find the Solidity SAI implementation [here](https://github.com/makerdao/sai/tree/master/src).
As part of this challenge you would have to port this implementation to ink!.

You don't have to mess around with any external Oracle, just mock the price.

To complete this milestone we expect:
* An implementation of SAI in ink!.
* Your implementation has to contain unit and integration tests so that we can assert that it behaves as advertised.


### Implement a command-line user interface to interact with a smart contract that is deployed to a chain.

We have a command-line interface (CLI) to interact with smart contracts that are deployed on a chain: [`cargo-contract`](https://github.com/paritytech/cargo-contract).
Its target audience are developers though and it's a general purpose tool.

What we would like to see is a command-line user interface that enables interacting with one particular contract in a user friendly way.

We think the ink! [multisig example](https://github.com/paritytech/ink/blob/master/examples/multisig) provides enough room for building a targeted CLI for users of that contract. 
You could think about how to abstract things away in your CLI.

To complete this challenge we expect:
* A command-line interface that eases interacting with ink!'s `multisig` example.
* Your tool has to use the [`subxt`](https://github.com/paritytech/subxt/) crate for this purpose. This is the same library used by `cargo-contract` for its `instantiate`, `upload`, and `call` sub-commands (see the [usage notes here](https://github.com/paritytech/cargo-contract#usage)). 

## Resources
### Substrate 

- [Tutorials](https://docs.substrate.io/tutorials/v3/)
    - [Build your first chain](https://docs.substrate.io/tutorials/v3/create-your-first-substrate-chain/)
    - [Launch a parachain](https://docs.substrate.io/tutorials/v3/cumulus/start-relay/)
- [How-to guides](https://docs.substrate.io/how-to-guides/v3/)
    - [Making an HTTP request from an off-chain worker](https://docs.substrate.io/how-to-guides/v3/ocw/http-requests/)
    - [Simple crowdfunding pallet](https://docs.substrate.io/how-to-guides/v3/pallet-design/crowdfund/)
- [Documentation](https://docs.substrate.io/v3/getting-started/overview/)
    - [Storage in Substrate](https://docs.substrate.io/v3/advanced/storage/)
    - [Off-chain workers](https://docs.substrate.io/v3/concepts/off-chain-features/#off-chain-workers)
### ink! 

- [ink! official documentation](https://paritytech.github.io/ink-docs/)
    - [ink! Contracts Workshop](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/) (3 parts)
    - [Why Webassembly for smart contracts?](https://paritytech.github.io/ink-docs/why-webassembly-for-smart-contracts)
    - [ink! vs. Solidity](https://paritytech.github.io/ink-docs/ink-vs-solidity)
- [OpenBrush](https://openbrush.io/): the OpenZepplin for ink! smart contracts. 
- [Patract labs](https://docs.patract.io/en/) Wasm contract development stack.

### Front-end development
- [Client libraries](https://docs.substrate.io/v3/integration/client-libraries/)
- [Substrate connect](https://docs.substrate.io/v3/integration/substrate-connect/)
- [Polkadot-JS API](https://polkadot.js.org/docs/)

### Oracles

Pallets:
- [`orml-oracle`](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/oracle)

Community projects:

- [DIA Wasm oracle project](https://github.com/diadata-org/dia-wasm-oracle)
- [DIA Oracle pallet](https://github.com/diadata-org/oracle-pallet/blob/master/runtime/src/lib.rs#L277-L326)
- [EVM and Substrate compatible](https://github.com/edgeware-network/edgeware-chainlink)

Use our dedicated [Substrate StackExchange](https://substrate.stackexchange.com/) to look for common issues or post your own question!