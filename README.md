# Foundry Fund Me

This is a crowdfunding contract.

## About

The FundMe contract is a decentralized crowdfunding contract built on Ethereum. It allows people to fund/donate ETH to the contract and its owner can retrieve all of it.
This is a training project learnt from the unavoidable Cyfrin Updraft. Learn from them too at https://updraft.cyfrin.io/.

## Getting Started

### Requirements

- [git](https://git-scm.com/)
- [foundry](https://getfoundry.sh/)

if you're on Windows you'll likely need WSL. Follow the Development Environment Setup for Windows at https://updraft.cyfrin.io/courses/foundry/foundry-simple-storage/development-environment-setup-windows.

### Installation

```
git clone https://github.com/Giovidoh/foundry-fund-me
cd foundry-fund-me
forge install
```

### Environment Setup

Create a .env file:

```
SEPOLIA_RPC_URL=your_rpc_url_here
PRIVATE_KEY=your_private_key_here
```

⚠️ Never commit your .env file.

PRIVATE_KEY is REALLY IMPORTANT and should not be shared especially when deploying to production. It's good to get the habit now with test environments.
It's better you use the keystore method to encrypt your PRIVATE_KEY instead of leaving it into the .env file.
Use this command to create a new keystore:

```
cast wallet import <ACCOUNT_NAME> --interactive
```

You'll be prompted to enter your private key and a password. Keep that password safe as you'll need it to use the encrypted PRIVATE_KEY in your future commands.
The new keystore is located at ~/.foundry/keystores/<ACCOUNT_NAME>
You can use the following command to list all your accounts:

```
cast wallet list
```

So if you need your private key in a command such as `forge create` you can use the `--account <ACCOUNT_NAME>`.
https://www.getfoundry.sh/reference/forge/create#forge-create

## Usage

### Run a local node

```
anvil
```

### Deploy locally

Load your .env file in the terminal:

```
source .env
```

Then:

```
forge script script/DeployFundMe.s.sol --rpc-url http://localhost:8545 --private-key $PRIVATE_KEY --broadcast
```

Or, if you're using keystore:

```
forge script script/DeployFundMe.s.sol --rpc-url http://localhost:8545 --account <ACCOUNT_NAME> --broadcast
```

### Deploy to Sepolia

```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast
```

Or, if you're using keystore:

```
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --account <ACCOUNT_NAME> --broadcast
```

## Testing

### Run all tests

```
forge test
```

### Run tests with verbosity

```
forge test -vvv
```

### Run tests on Sepolia fork

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test coverage

```
forge coverage
```

## What I Learned

- How to use Chainlink Price Feeds to get off-chain ETH/USD data
- How to create and get my Local Price Feeds
- How to write unit and integration tests with Foundry
- How to use vm.prank, vm.deal, vm.expectRevert cheatcodes
- How to deploy contracts using forge script
- How to secure private keys using cast wallet keystores

## License

MIT
