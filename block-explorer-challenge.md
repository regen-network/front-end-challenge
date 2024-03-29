# Block Explorer Code Challenge

This challenge consists of building a simplified version of a block explorer for [Regen Ledger](https://github.com/regen-network/regen-ledger) (built on top of [Cosmos SDK](https://github.com/cosmos/cosmos-sdk)) using React and TypeScript.

The goal here is for us to get a basic understanding of how you code, so it's not meant to be very difficult. Ideally you shouldn't spend more than a few hours on it.

## Setup 

We recommend starting from a basic template (e.g. [create-react-app](https://reactjs.org/docs/create-a-new-react-app.html), or something similar) -- though it's also fine if you have a different preferred way of bootstrapping a project.

## App

Write a basic single page application that displays the list of recent blocks for [Regen Redwood Testnet](https://docs.regen.network/ledger/get-started/live-networks.html#redwood-testnet). You can use this RPC endpoint http://redwood.regen.network:26657/ to query relevant data based on [Tendermint RPC documentation](https://docs.tendermint.com/master/rpc/).

We recommend to use https://github.com/cosmos/cosmjs to get latest blocks info, in particular https://cosmos.github.io/cosmjs/latest/stargate/classes/StargateClient.html which is a client for the Cosmos SDK "Stargate" release.
If you choose to use Webpack 5, please make sure to update the config accordingly: https://github.com/cosmos/cosmjs#webpack-configs

You can have a look at Aneka block explorer for some inspiration: https://redwood.regen.aneka.io/

Ideally your submission should involve a component-based approach, and have a responsive layout (optimising for both mobile and web views).

*Optional:*

Show the blocks transactions details if any.

In Cosmos SDK, [transactions](https://docs.cosmos.network/master/core/transactions.html) consist of 1 or more signed [`sdk.Msg`'s](https://docs.cosmos.network/master/building-modules/messages-and-queries.html#messages) which are objects whose end-goal is to trigger state transitions.

https://cosmos.github.io/cosmjs/latest/proto-signing/ provides some utility functions to decode [transaction raw data](https://cosmos.github.io/cosmjs/latest/proto-signing/modules.html#decodeTxRaw) as well as transaction `Msg`'s using a [Registry](https://cosmos.github.io/cosmjs/latest/proto-signing/classes/Registry.html) instantiated with Stargate [defaultRegistryTypes](https://cosmos.github.io/cosmjs/latest/stargate/modules.html#defaultRegistryTypes). Supported `Msg` types are registered within this Registry which then provides methods for decoding/encoding such `Msg`s.

## What we're looking for

With this challenge we're trying to get a sense of how you would architect a basic front end application that interacts with a blockchain. We're not looking for anything visually innovative, but do appreciate clean design. That being said, this is a coding challenge, not a design challenge - so code readability, and clean architecture are the main things we will be paying attention to.

## Submission

For submission, please send us an email with a link to your project, ideally as a github repo. Oh, and don't forget to add a nice README.md so we know how to build & run it :)
