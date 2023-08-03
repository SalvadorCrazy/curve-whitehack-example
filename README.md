# Curve Whitehack example 30/07/2023

Based on [Whitehacks Kit](https://github.com/emilianobonassi/whitehacks-kit), adapted from [SunWeb3Sec](https://github.com/SunWeb3Sec/DeFiHackLabs/blob/main/src/test/Curve_exp01.sol) (thanks!) 

## Disclaimer

Provided AS-IS as educational content only, disclaim any liability for using it.

## Usage

Whitehacks are hard and should be execute by professionals. If you are unsure reach-out [ETHSecurity tg channel](https://t.me/ETHSecurity). Reach-out anyway.

This repo offers a guide to prepare them.

They must be executed in 1 shot and privately, hence one single transaction and the private mempool by Flashbots.

You prepare, you test in a fork, you don't change, you execute.

## Setup

0. Fork the repo
1. [Install Foundry](https://book.getfoundry.sh/getting-started/installation)
2. Edit [Whitehack.sol](./src/Whitehack.sol)
3. Adapt [Whitehack.s.sol](./script/Whitehack.s.sol) 

## Preparation

1. Unset `$RPC_URL`

```zsh
unset $RPC_URL
```

2. Check no RPC port open on your computer, if so kill the processes

```zsh
netstat -an | grep LISTEN | grep 8545
```

## Test

1. Run Anvil fork with 

```zsh
anvil --fork-url https://eth.llamarpc.com --fork-block-number 17806055
```

2. Impersonate your account `0xYOUR_WALLET_ADDRESS` 

```zsh
cast rpc \
    anvil_impersonateAccount "0xYOUR_WALLET_ADDRESS" \
    --rpc-url "http://localhost:8545"
```

3. Run the script

```zsh
forge script \
  script/Whitehack.s.sol:WhitehackScript \
  --rpc-url "http://localhost:8545" \
  --sender "0xYOUR_WALLET_ADDRESS" \
  -vvv \
  --broadcast
```