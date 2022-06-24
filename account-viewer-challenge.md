# Account Viewer Code Challenge

This challenge consists of building a single page application integrated with [Keplr](https://wallet.keplr.app/) wallet that shows the user REGEN account balance using React and 
TypeScript.

The goal here is for us to get a basic understanding of how you code, so it's not meant to be very difficult. Ideally you shouldn't spend more than a few hours on it.

## Setup 

We recommend starting from a basic template (e.g. [create-react-app](https://reactjs.org/docs/create-a-new-react-app.html), or something similar) -- though it's also fine if you have a different preferred way of bootstrapping a project.

Make sure to have [Keplr browser extension](https://chrome.google.com/webstore/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap?hl=en) installed and setup.

## App

Write a basic single page application that connects to Keplr and displays your account balance on [Regen Redwood Testnet](https://docs.regen.network/ledger/get-started/live-networks.html#redwood-testnet). For the purpose of this exercise, let's assume that the end user already has Keplr installed.

In order to add Regen Redwood Testnet to Keplr, you'll need to use Keplr ["Suggest Chain" feature](https://docs.keplr.app/api/suggest-chain.html) with the following parameters: 
```ts
{
  // Chain-id of the Regen chain.
  chainId: 'regen-redwood-1',
  // The name of the chain to be displayed to the user.
  chainName: 'Regen Redwood Testnet',
  // RPC endpoint of the chain.
  rpc: 'http://redwood.regen.network:26657/',
  // REST endpoint of the chain.
  rest: 'http://redwood.regen.network:1317/',
  // Staking coin information
  stakeCurrency: {
    // Coin denomination to be displayed to the user.
    coinDenom: 'REGEN',
    // Actual denom (i.e. uatom, uscrt) used by the blockchain.
    coinMinimalDenom: 'uregen',
    // # of decimal points to convert minimal denomination to user-facing denomination.
    coinDecimals: 6,
    // (Optional) Keplr can show the fiat value of the coin if a coingecko id is provided.
    // You can get id from https://api.coingecko.com/api/v3/coins/list if it is listed.
    // coinGeckoId: ""
  },
  // (Optional) If you have a wallet webpage used to stake the coin then provide the url to the website in `walletUrlForStaking`.
  // The 'stake' button in Keplr extension will link to the webpage.
  // walletUrlForStaking: "",
  // The BIP44 path.
  bip44: {
    // You can only set the coin type of BIP44.
    // 'Purpose' is fixed to 44.
    coinType: 118,
  },
  // Bech32 configuration to show the address to user.
  bech32Config: {
    bech32PrefixAccAddr: 'regen',
    bech32PrefixAccPub: 'regenpub',
    bech32PrefixValAddr: 'regenvaloper',
    bech32PrefixValPub: 'regenvaloperpub',
    bech32PrefixConsAddr: 'regenvalcons',
    bech32PrefixConsPub: 'regenvalconspub',
  },
  // List of all coin/tokens used in this chain.
  currencies: [
    {
      // Coin denomination to be displayed to the user.
      coinDenom: 'REGEN',
      // Actual denom (i.e. uatom, uscrt) used by the blockchain.
      coinMinimalDenom: 'uregen',
      // # of decimal points to convert minimal denomination to user-facing denomination.
      coinDecimals: 6,
      // (Optional) Keplr can show the fiat value of the coin if a coingecko id is provided.
      // You can get id from https://api.coingecko.com/api/v3/coins/list if it is listed.
      // coinGeckoId: ""
    },
  ],
  // List of coin/tokens used as a fee token in this chain.
  feeCurrencies: [
    {
      // Coin denomination to be displayed to the user.
      coinDenom: 'REGEN',
      // Actual denom (i.e. uatom, uscrt) used by the blockchain.
      coinMinimalDenom: 'uregen',
      // # of decimal points to convert minimal denomination to user-facing denomination.
      coinDecimals: 6,
      // (Optional) Keplr can show the fiat value of the coin if a coingecko id is provided.
      // You can get id from https://api.coingecko.com/api/v3/coins/list if it is listed.
      // coinGeckoId: ""
    },
  ],
  // (Optional) The number of the coin type.
  // This field is only used to fetch the address from ENS.
  // Ideally, it is recommended to be the same with BIP44 path's coin type.
  // However, some early chains may choose to use the Cosmos Hub BIP44 path of '118'.
  // So, this is separated to support such chains.
  coinType: 118,
  // (Optional) This is used to set the fee of the transaction.
  // If this field is not provided, Keplr extension will set the default gas price as (low: 0.01, average: 0.025, high: 0.04).
  // Currently, Keplr doesn't support dynamic calculation of the gas prices based on on-chain data.
  // Make sure that the gas prices are higher than the minimum gas prices accepted by chain validators and RPC/REST endpoint.
  gasPriceStep: {
    low: 0.01,
    average: 0.025,
    high: 0.04,
  },
  features: ['stargate'],
}
```

Here's Keplr API documentation: https://docs.keplr.app/api/

Then, in order to query your account balance, you can use our RPC endpoint http://redwood.regen.network:26657/ along with:
- either our JS library for interacting with Regen Ledger: https://github.com/regen-network/regen-js, in particular [the bank module (`x/bank`) query service](https://github.com/regen-network/regen-js/blob/main/packages/api/proto/cosmos/bank/v1beta1/query.proto)
- or [CosmJS](https://github.com/cosmos/cosmjs), in particular https://cosmos.github.io/cosmjs/latest/stargate/classes/StargateClient.html which is a client for [Cosmos-SDK](https://github.com/cosmos/cosmos-sdk) Stargate release.

If you choose to use Webpack 5, please make sure to update the config accordingly: https://github.com/cosmos/cosmjs#webpack-configs

Here's some additional documentation about `x/bank` client: https://docs.cosmos.network/master/modules/bank/06_client.html#

You can use this faucet to get some tokens to play with: 
```sh
curl http://209.182.218.23:8000/faucet/<addr>
```

Ideally your submission should involve a component-based approach, and have a responsive layout (optimising for both mobile and web views).

## What we're looking for

With this challenge we're trying to get a sense of how you would architect a basic front end application that interacts with a blockchain. We're not looking for anything visually innovative, but do appreciate clean design. That being said, this is a coding challenge, not a design challenge - so code readability, and clean architecture are the main things we will be paying attention to.

## Submission

For submission, please send us an email with a link to your project, ideally as a github repo. Oh, and don't forget to add a nice README.md so we know how to build & run it :)
