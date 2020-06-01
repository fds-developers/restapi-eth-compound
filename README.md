# restapi-eth-compound

## REST API calling an ETH Compound Smart Contract

Sample code for building your own REST API calling the Compound Ethereum smart contract API. Made with Express.js, Infura, Web3.js and local blockchain sandbox provided by Ganache-cli

The REST API abstracts away all interactions with the blockchain and dealing with private keys.

Built using [Node.js](https://nodejs.org/en/download/)

https://compound.finance/docs#guides

You can test safely using a local blockchain fork using ganache-cli and Infura (you need to create a free account at infura.io)

There is a video you can watch going over setting up everything and how to use this https://pages.consensys.net/build-your-own-ethereum-api-with-infura-and-compound

## Setup our NodeJs dependencies and configuration

```
npm install
```

**config.json**

The listed contract addresses and ABIs might be out of date. They can be confirmed here https://compound.finance/docs#networks.

**server.js**

1. Be sure to set an environment variable for the Ethereum wallet private
key.

2. Replace the values in the .env file (launch ganache cli, see below and enter your wallet private key string in .env)

## Setup Ganache CLI

```
# generates a new private key each time
ganache-cli -f https://mainnet.infura.io/v3/PROJECT_ID -i 999

# uses the mnemonic and that way, it uses that private key each time
ganache-cli -f https://mainnet.infura.io/v3/PROJECT_ID -i 999 -m "mnemonic"
```

## Running

```
npm start
```

## REST API example calls

```bash
curl localhost:3000/wallet-balance/eth/
curl localhost:3000/wallet-balance/ceth/
curl localhost:3000/supply/eth/3
curl localhost:3000/protocol-balance/eth/
curl localhost:3000/redeem/eth/123
```

See below some sample outputs for a series of API calls. The Ganache wallet always starts out with 100 ETH.

```bash
curl localhost:3000/wallet-balance/eth/
> 100

curl localhost:3000/wallet-balance/ceth/
> 0

curl localhost:3000/supply/eth/5
> OK

curl localhost:3000/protocol-balance/eth/
> 4.999999999885010676

curl localhost:3000/wallet-balance/eth/
> 94.99788632

curl localhost:3000/wallet-balance/ceth/
> 249.85542658

curl localhost:3000/redeem/eth/249.85542658
> OK

curl localhost:3000/protocol-balance/eth/
> 0

curl localhost:3000/wallet-balance/ceth/
> 0

curl localhost:3000/wallet-balance/eth/
> 99.995909700269046879

```

## documentation

cETH contract address https://etherscan.io/token/0x4ddc2d193948926d02f9b1fe9e1daa0718270ed5

https://compound.finance/docs/ctokens#underlying_balance

https://github.com/compound-developers/api-guide-example

## sources

https://medium.com/compound-finance/compound-ethereum-api-with-infura-1f5c555fd4a2

https://pages.consensys.net/build-your-own-ethereum-api-with-infura-and-compound
