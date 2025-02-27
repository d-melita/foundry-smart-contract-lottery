# Smart Contract Lottery

This is a simple smart contract lottery system that allows users to enter a lottery by sending a certain amount of ether to the contract. The contract will then randomly select a winner and send the prize money to the winner automatically.

This project was made as part of the [Foundry 101 Course](https://updraft.cyfrin.io/courses/foundry). You can check the course
repo [here](https://github.com/Cyfrin/foundry-full-course-cu) and the source code of the original project [here](https://github.com/Cyfrin/foundry-smart-contract-lottery-cu/tree/main).

## Getting Started

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

## Quickstart

```
git clone https://github.com/d-melita/foundry-smart-contract-lottery.git
cd foundry-smart-contract-lottery
```

## Usage

### Installation

```
make install
```

### Compiling

```
make build
```

### Testing

To test locally, run the following command:

```
make test
```

To test on a fork testnet, run the following command:

```
forge test --fork-url $SEPOLIA_RPC_URL
```

Be sure to create a `.env` file where you populate the following environment variables:

```
SEPOLIA_RPC_URL=<your-sepolia-rpc-url-from-alchemy>
```

### Test Coverage

```
forge coverage
```

### Deploying

#### Locally

To deploy locally, run the following command on a terminal window:

```
make anvil
```

And then run the following command on a separate terminal window:

```
make deploy
```

Be sure to add the following line to your `.env` file:

```
DEFAULT_ANVIL_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
```

#### On Sepolia

To deploy to a fork testnet, run the following command:

```
make deploy ARGS="--network-sepolia"
```

Be sure to create a `.env` file where you populate the following environment variables:

```
SEPOLIA_RPC_URL=<your-sepolia-rpc-url-from-alchemy>
ETHERSCAN_API_KEY=<your-etherscan-api-key-for-validation>
PRIVATE_KEY=<your-TESTING-private-key-with-no-funds-associated>
```

Optionally, instead of using a private key, you can use `cast` to create an account associated with a privat key.
To do so, run the following:

```
cast wallet import <name-of-the-account> --interactive
```

Then paste your private key and create a password you will remember.

After this, modify the `Makefile` to the following:

```Makefile
ifeq ($(findstring --network sepolia,$(ARGS)),--network sepolia)
	NETWORK_ARGS := --rpc-url $(SEPOLIA_RPC_URL) --account $(ACCOUNT) --broadcast --verify --etherscan-api-key $(ETHERSCAN_API_KEY) -vvvv
endif
```

and add the following line to your `.env` file:

```
ACCOUNT=<name-of-the-account>
```

And don't forget to delete the `PRIVATE_KEY` variable from the `.env` file.

## Estimate gas

You can estimate how much gas things cost by running:

```
make snapshot
```

# Formatting

To run code formatting:

```
make fmt
```

## Problems

For any problems encountered, I suggested checking the [Discussion tab](https://github.com/Cyfrin/foundry-full-course-cu/discussions) of the course repo.
