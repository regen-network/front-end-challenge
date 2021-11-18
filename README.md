# Front-End Code Challenge

This challenge consists of building a simplified version of a block explorer for [Regen Ledger](https://github.com/regen-network/regen-ledger) using React and TypeScript.

The goal here is for us to get a basic understanding of how you code, so it's not meant to be very difficult. Ideally you shouldn't spend more than a few hours on it.

## Setup 

We recommend starting from a basic template (e.g. [create-react-app](https://reactjs.org/docs/create-a-new-react-app.html), or something similar) -- though it's also fine if you have a different preferred way of bootstrapping a project.

## App

Write a basic single page application that displays the list of recent blocks for [Regen Hambach Testnet](https://docs.regen.network/getting-started/live-networks.html#hambach-testnet). You can use this RPC endpoint http://hambach.regen.network:26657/ to query relevant data based on [Tendermint RPC documentation](https://docs.tendermint.com/master/rpc/).

We recommend to use https://github.com/cosmos/cosmjs to get latest blocks info, in particular https://cosmos.github.io/cosmjs/latest/stargate/classes/signingstargateclient.SigningStargateClient.html

You can have a look at Aneka block explorer for some inspiration: https://hambach.regen.aneka.io/

Ideally your submission should involve a component-based approach, and have a responsive layout (optimising for both mobile and web views).

*Optional:*

Show the blocks transactions details if any. https://cosmos.github.io/cosmjs/latest/proto-signing/modules/decode.html provides some utility functions to decode transaction raw data.

## What we're looking for

With this challenge we're trying to get a sense of how you would architect a basic front end application that interacts with a blockchain. We're not looking for anything visually innovative, but do appreciate clean design. That being said, this is a coding challenge, not a design challenge - so code readability, and clean architecture are the main things we will be paying attention to.

## Submission

For submission, please send us an email with a link to your project, ideally as a github repo. Oh, and don't forget to add a nice README.md so we know how to build & run it :)
