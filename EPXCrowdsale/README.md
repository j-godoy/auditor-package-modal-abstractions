# EPXCrowdsale Smart Contract

This repository contains the Solidity smart contract for the EPXCrowdsale. The contract is designed to manage the presale and ICO token sale for the EPX token.

## Overview

The EPXCrowdsale contract is responsible for handling the sale of EPX tokens. It includes functionality for setting up the crowdsale, accepting contributions, distributing tokens, and handling refunds if the funding goal is not met.

## Features

- **Ownership and Administration**: The contract includes an `owned` contract that manages ownership and administrative privileges.
- **SafeMath**: The contract uses a `safeMath` library to perform safe arithmetic operations.
- **Token Management**: The contract interacts with a standard ERC20 token contract to manage token balances and transfers.
- **Crowdsale Setup**: The contract allows the owner to set up the crowdsale parameters, including the start and end blocks, funding goals, and token supply.
- **Contribution Handling**: The contract accepts contributions in Ether, calculates the number of tokens to be distributed based on the current price, and transfers the tokens to the contributor.
- **Refunds**: If the funding goal is not met, contributors can request a refund of their Ether, and their tokens will be burned.
- **Events**: The contract emits events for token purchases, refunds, and token burns.

### StandardToken Contract

The `StandardToken` contract is an interface for the ERC20 token used as a reward in the crowdsale.

### EPXCrowdsale Contract

The `EPXCrowdsale` contract includes the following key functions:

- **constructor**: Initializes the contract and sets the admin address.
- **initialEPXSupply**: Returns the initial supply of EPX tokens.
- **remainingEPXSupply**: Returns the remaining supply of EPX tokens.
- **SetupCrowdsale**: Sets up the crowdsale parameters.
- **checkPrice**: Returns the current price of EPX tokens based on the block number.
- **buy**: Accepts contributions and distributes tokens to the contributor.
- **beneficiaryMultiSigWithdraw**: Allows the owner to withdraw funds to the beneficiary wallet if the funding goal is met.
- **checkGoalReached**: Checks if the funding goal is reached and updates the contract status.
- **refund**: Allows contributors to request a refund if the funding goal is not met.


## Usage

1. Contributors can send Ether to the contract address to purchase EPX tokens.
2. The owner can call the `checkGoalReached` function to check the funding status.
3. If the funding goal is met, the owner can withdraw funds to the beneficiary wallet.
4. If the funding goal is not met, contributors can call the `refund` function to get their Ether back.



## Abstractions

There are two abstractions:
 - EPXCrowdsale: this is the default abstraction, using the `CurrentStatus` simil to an enum, as a predicate abstraction.
 - EPXCrowdsale+EPA: this is the default abstraction, using the EPA predicate abstraction.
 - EPXCrowdsale+EPA+isCrowdSaleClosed: this is the abstraction using the EPA predicate abstraction, plus `isCrowdSaleClosed` boolean value as predicate.