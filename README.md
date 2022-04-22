# Substrate and Polkadot hacker kit 💻 🛠

## Welcome! 👋 😃

This repository is made for hackathon participants looking to work on some Substrate / Polkadot challenges for the [Chainlink Hackathon 2022](https://chainlinkspring2022.devpost.com/).

What's what?

* [Substrate](substrate.io) is a framework that makes it easy to create custom blockchains and runtime logic.
* [Polkadot](https://polkadot.network/) is an upgradable blockchain built with Substrate, designed to secure other chains connected to it and provide interoperability among them.
* [ink!](https://paritytech.github.io/ink-docs/) is a special language designed to make it easy to write Wasm smart contracts for Substrate chains.

🔎 Are you looking for some bounties to work on? Head over to the [challenges page](./challenges/README.md) and discover what we suggest working on to win from a prize pool of $75k.

📚 Are you new to Substrate and Polkadot? Brush up your knowledge by [going through these useful resources](#resources).

💬 Have questions? Look for common questions in our dedicated [Substrate Stack Exchange](https://substrate.stackexchange.com/) or post your own question if you can't find an answer for it anywhere. Otherwise, we're happy to help you directly in our Discord support channel.


**Note:** Use the challenge ideas as guidance for the types of projects we'd like to see built. And if one of our ideas is something you'd like to do, go for it! 
The intention is that these challenge ideas inspire you to work on prize-winning submissions that you will enjoy working on.

-------------

## Resources 📚

Here are some useful resources that will help you learn the skills you need to be successful in working with Polkadot, ink! and Substrate.
### 🔦 Substrate

Even those of you working more on the front-end side of things, you'll need to understand basic concepts about Substrate and how to work with them. These links will help you acquire the knowledge you'll need to build with Substrate.

- [Tutorials](https://docs.substrate.io/tutorials/v3/). From more beginner to more advanced, a number of tutorials exist to get you familiar with building with Substrate. We recommend you get through as many as you can - here are some we recommend you do to prepare you for some of our challenges:
    - [Build your first chain](https://docs.substrate.io/tutorials/v3/create-your-first-substrate-chain/)
    - [Launch a parachain](https://docs.substrate.io/tutorials/v3/cumulus/start-relay/)
- [How-to guides](https://docs.substrate.io/how-to-guides/v3/). Guides will help you solve specific problems and "get right to it". Here are a few that will be relevant to some of you:
    - [Making an HTTP request from an off-chain worker](https://docs.substrate.io/how-to-guides/v3/ocw/http-requests/)
    - [Simple crowdfunding pallet](https://docs.substrate.io/how-to-guides/v3/pallet-design/crowdfund/)
- [Documentation](https://docs.substrate.io/v3/getting-started/overview/). The reference material will help you grasp the conceptual knowledge you'll need. Here are some articles we recommend you go through:
    - [Storage in Substrate](https://docs.substrate.io/v3/advanced/storage/)
    - [Off-chain workers](https://docs.substrate.io/v3/concepts/off-chain-features/#off-chain-workers)
### 🦑 ink!

A lot of our challenges this year put ink! in the spotlight. We recommend you complete the ink! workshop but also learn from the extensive docs maintained by the ink! team.
- [ink! official documentation](https://paritytech.github.io/ink-docs/)
    - [ink! Contracts Workshop](https://docs.substrate.io/tutorials/v3/ink-workshop/pt1/) (3 parts)
    - [Why Webassembly for smart contracts?](https://paritytech.github.io/ink-docs/why-webassembly-for-smart-contracts)
    - [ink! vs. Solidity](https://paritytech.github.io/ink-docs/ink-vs-solidity)
- [OpenBrush](https://openbrush.io/): the OpenZepplin for ink! smart contracts. 
- [Patract labs](https://docs.patract.io/en/) Wasm contract development stack.

### 👨‍💻 Front-end development

Are you coming in as a front-end developer? There's lots of resources out there including ecosystem projects building libraries for both mobile and browser based applications. Here's a good place to start if that's what you're here for:

- [Client libraries](https://docs.substrate.io/v3/integration/client-libraries/): discover existing client libraries in different languages.
- [Substrate connect](https://docs.substrate.io/v3/integration/substrate-connect/): learn about the power of integrating Substrate connect into your applications.
- [Polkadot-JS API](https://polkadot.js.org/docs/): jump right into the Polkadot JS API documentation (its very comprehensive!).
- [Kitties Front-end tutorial](https://docs.substrate.io/tutorials/v3/kitties/pt2/): follow this tutorial to guide you through building a front-end for the Kitties pallet (an NFT-like pallet) built using the Polkadot JS API.

### 🔮 Oracle related community projects

There are some projects out there doing similar things to some of the challenges proposed for the various Polkadot tracks. Have a look at whats being done already - you might have an "a-ha" moment by looking through these: 

- The [Chainlink feed pallet](https://github.com/smartcontractkit/chainlink-polkadot): a Chainlink <> Polkadot integration (it's very out of date though).
- Pallet [`orml-oracle`](https://github.com/open-web3-stack/open-runtime-module-library/tree/master/oracle): a pallet that will give your chain oracle capabilities.
- [DIA Wasm oracle project](https://github.com/diadata-org/dia-wasm-oracle) and [DIA Oracle pallet](https://github.com/diadata-org/oracle-pallet/blob/master/runtime/src/lib.rs#L277-L326): have a look at this project enabling oracle interaction for Wasm smart contracts.
- [EVM and Substrate compatible Chainlink contract](https://github.com/edgeware-network/edgeware-chainlink)