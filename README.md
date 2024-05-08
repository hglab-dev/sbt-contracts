# @bisonai/sbt-contracts

This repository defines Solidity smart contracts, deployment, and test scripts for Soulbound token (SBT). The implementation follows [EIP-5192: Minimal Soulbound NFT](https://eips.ethereum.org/EIPS/eip-5192).

## Installation

```
yarn install
```

## Prerequisites

1. Generate mnemonic if you do not have any.

```
npx mnemonics
```

2. Create `.env` from `.env.example`.

```
cp .env.example .env
```

3. Fill in generated mnemonic to `MNEMONIC` environment variable.

## Compilation

```
yarn compile
```

## Predefined networks

`hardhat.config.ts` predefines several networks where SBT can be deployed.
Currently, you can deploy your SBT to `localhost`, `baobab` or `cypress` networks.
If you want to deploy to any other network, simply add connection information to `hardhat.config.ts`.

## Deploy SBT

To deploy your SBT call `yarn deploy` command and set options `--base-uri`, `--name` and `--symbol`.
If you want to deploy to specific network you can define it using `--network` option.
To find more information about networks, go to [Predefined networks](#predefined-networks) section.

```
Hardhat version 2.10.1

Usage: hardhat [GLOBAL OPTIONS] deploy --base-uri <STRING> --name <STRING> --symbol <STRING>

OPTIONS:

  --base-uri    URI (must end with /) that will be used as prefix when returning tokenURI
  --name        SBT name
  --symbol      SBT symbol

deploy: Deploy SBT

For global options help run: hardhat help
```

### Example of deploying SBT in localhost network

```
yarn deploy \
    --name MySBT \
    --symbol MSBT \
    --base-uri "http://localhost/" \
    --network localhost
```

yarn deploy --name rpcTestSBT --symbol RTST --base-uri "https://dev.readyplayerclub.com/api/rpc-sbt/" --network ethereumSepolia

yarn deploy --name rpcTestSBT --symbol RTST --base-uri "https://www.readyplayerclub.com/api/rpc-badge/" --network ethereumSepolia


yarn deploy --name rpcSBT --symbol RSBT --base-uri "https://www.readyplayerclub.com/api/rpc-sbt/" --network matic

SBT was deployed to matic network and can be interacted with at address 0x19376d02631Cef85098bCf671FC347dD6479cD05

### Output

```
SBT was deployed to localhost network and can be interacted with at address 0xd65C849d9ADf21bc83cD8dEC377C4f0181dEcE6B
```

## Mint SBT

When minting SBT, specify address of deployed SBT with `--address` option, address that will receive SBT token with `--to` option and ID of token with `--token-id` option.
Do not forget that single account can hold only single SBT token and that ID of every token is unique and cannot be reused.
After SBT token is minted to a specified account, it cannot be transferred to any other one.

```
Hardhat version 2.10.1

Usage: hardhat [GLOBAL OPTIONS] mint --address <STRING> --to <STRING> --token-id <STRING>

OPTIONS:

  --address     Address of deployed SBT
  --to          Address receiving SBT token
  --token-id    ID of SBT token that is being minted

mint: Mint SBT

For global options help run: hardhat help
```

### Example of minting SBT in localhost network

```
yarn mint \
    --address 0xd65C849d9ADf21bc83cD8dEC377C4f0181dEcE6B \
    --to 0xeaeF3D4964F40924D3082CFcB6F7E1d9Fe5D299B \
    --token-id 123  \
    --network localhost
```

yarn mint --address 0x7AEc00E76ED7533A22351ef3B99c0898cC1203Ad --to 0x1d9136fa6c577aDBf437dB4e63dc216D331289e6 --token-id 2 --network ethereumSepolia

yarn mint --address 0xf405B7081f9dA5a99708E91cf08b51fAcAe3E8d6 --to 0x1d9136fa6c577aDBf437dB4e63dc216D331289e6 --token-id 1 --network ethereumSepolia

yarn mint --address 0x356895083d7d8cC98AD935698ad21FEeB7780a17 --to 0xB3506D27B8A3141bB3a33031c1cF6b1069957bf3 --token-id 1004 --network ethereumSepolia

yarn mint --address 0x19376d02631Cef85098bCf671FC347dD6479cD05 --to 0x1d9136fa6c577aDBf437dB4e63dc216D331289e6 --token-id 0 --network matic

yarn mint --address 0x19376d02631Cef85098bCf671FC347dD6479cD05 --to 0x9753a6122349933f933c0fe6200E67BBB1199C09 --token-id 1 --network matic






### Output

```
SBT with tokenId 123 was minted for address 0xeaeF3D4964F40924D3082CFcB6F7E1d9Fe5D299B
```

## Run test

Before running test, make sure you compile your smart contracts.

```
yarn test
```

## Publish to registry

```
yarn clean
yarn compile
yarn build
yarn pub
```

## License

[Apache License 2.0](LICENSE)
