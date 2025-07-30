# EscrowVault Smart Contract

The `EscrowVault` smart contract is designed to manage funds collected during a crowdsale. It allows for the collection of ethers, the ability to refund investors if a soft cap is not reached, and the transfer of funds to a beneficiary once the goal is achieved.

## Features

- **SafeMath Library**: Utilizes the `SafeMath` library to perform safe mathematical operations.
- **Ownable Contract**: Inherits from the `Ownable` contract to manage ownership and permissions.
- **State Management**: Manages different states of the contract (`Active`, `Refunding`, `GoalReached`, `Closed`).
- **Deposits**: Allows the owner to deposit funds on behalf of investors.
- **Goal Management**: Allows the owner to set the goal as reached.
- **Withdrawals**: Allows the super owner to withdraw funds once the goal is reached.
- **Refunds**: Enables refunds to investors if the goal is not reached.


#### State Enum

Defines the possible states of the contract:
- `Active`: The contract is active and accepting deposits.
- `Refunding`: The contract is in a state where refunds are enabled.
- `GoalReached`: The funding goal has been reached.
- `Closed`: The contract is closed.

#### Variables

- `deposited`: A mapping to track the amount of ether deposited by each investor.
- `beneficiary`: The address of the beneficiary who will receive the funds.
- `superOwner`: The address of the super owner with special permissions.
- `state`: The current state of the contract.

#### Events

- `GoalReached`: Emitted when the funding goal is reached.
- `RefundsEnabled`: Emitted when refunds are enabled.
- `Refunded`: Emitted when an investor is refunded.
- `Withdrawal`: Emitted when funds are withdrawn.
- `Close`: Emitted when the contract is closed.

#### Functions

- `constructor`: Initializes the contract with the super owner and beneficiary addresses.
- `deposit`: Allows the owner to deposit funds on behalf of an investor.
- `setGoalReached`: Allows the owner to set the goal as reached.
- `withdraw`: Allows the super owner to withdraw a specified amount of funds.
- `withdrawAll`: Allows the owner to withdraw all funds.
- `close`: Closes the contract and withdraws all funds.
- `enableRefunds`: Enables refunds for investors.
- `refund`: Refunds the deposited amount to an investor.

## Usage

1. **Deployment**: Deploy the contract with the super owner and beneficiary addresses.
2. **Deposits**: The owner can deposit funds on behalf of investors.
3. **Goal Management**: The owner can set the goal as reached.
4. **Withdrawals**: The super owner can withdraw funds once the goal is reached.
5. **Refunds**: If the goal is not reached, the owner can enable refunds, and investors can be refunded.



## Abstractions

There are two abstractions:
 - EscrowVault: this is the default abstraction, using the values of the enum as predicates.
 - EscrowVault+EPA: this is the default abstraction, using the EPA predicate abstraction.