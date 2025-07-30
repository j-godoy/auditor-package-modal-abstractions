# ValidatorAuction Smart Contract

This repository contains the `ValidatorAuction` smart contract, which facilitates an auction where participants bid to become validators by depositing Ether. The contract manages the auction process, including starting the auction, accepting bids, and transitioning states based on the number of participants and the auction's duration. The DepositLocker contract ensures that deposits are securely managed, allowing for slashing of misbehaving validators and enabling withdrawals after a specified release time.

## Contracts Overview

### Ownable

The `Ownable` contract provides basic authorization control functions. It simplifies the implementation of user permissions by assigning an owner to the contract.

- **owner**: The address of the contract owner.
- **onlyOwner**: A modifier to restrict access to certain functions to the owner only.
- **transferOwnership**: Allows the current owner to transfer control of the contract to a new owner.

### DepositLockerInterface

An interface for the `DepositLocker` contract, defining the `slash` function.

### DepositLocker

The `DepositLocker` contract manages deposits from auction participants. It includes functionality for initializing the contract, registering depositors, handling deposits, allowing withdrawals, and slashing deposits.

- **initialized**: Indicates if the contract has been initialized.
- **deposited**: Indicates if deposits have been made.
- **slasher**: The address allowed to call the `slash` function.
- **depositorsProxy**: The address that registers depositors and deposits value on their behalf.
- **releaseTimestamp**: The timestamp after which deposits can be withdrawn.
- **canWithdraw**: A mapping of addresses to their withdrawal status.
- **numberOfDepositors**: The total number of registered depositors.
- **valuePerDepositor**: The value deposited per depositor.

#### Key Functions

- **init**: Initializes the contract with a release timestamp, slasher address, and depositors proxy address.
- **registerDepositor**: Registers a new depositor.
- **deposit**: Handles deposits from the depositors proxy.
- **withdraw**: Allows depositors to withdraw their funds after the release timestamp.
- **slash**: Slashes the deposit of a specified depositor.

### ValidatorAuction

The `ValidatorAuction` contract manages the auction process for validator slots. It includes functionality for starting the auction, placing bids, closing the auction, and handling deposits.

- **auctionDurationInDays**: The duration of the auction in days.
- **startPrice**: The starting price of the auction.
- **minimalNumberOfParticipants**: The minimum number of participants required for the auction.
- **maximalNumberOfParticipants**: The maximum number of participants allowed in the auction.
- **auctionState**: The current state of the auction.
- **depositLocker**: The `DepositLocker` contract instance.
- **whitelist**: A mapping of addresses that are allowed to participate in the auction.
- **bids**: A mapping of addresses to their bid amounts.
- **bidders**: An array of addresses that have placed bids.
- **startTime**: The start time of the auction.
- **closeTime**: The close time of the auction.
- **lowestSlotPrice**: The lowest price for a slot in the auction.

#### Key Functions

- **bid**: Allows participants to place bids in the auction.
- **startAuction**: Starts the auction.
- **depositBids**: Deposits the bids into the `DepositLocker` contract.
- **closeAuction**: Closes the auction.
- **addToWhitelist**: Adds addresses to the whitelist.
- **withdraw**: Allows participants to withdraw their bids after the auction ends or fails.
- **currentPrice**: Returns the current price of a slot based on the elapsed time.
- **priceAtElapsedTime**: Calculates the price of a slot based on the elapsed time.
- **withdrawAfterAuctionEnded**: Handles withdrawals after the auction ends.
- **withdrawAfterAuctionFailed**: Handles withdrawals after the auction fails.
- **transitionToDepositPending**: Transitions the auction state to `DepositPending`.
- **transitionToAuctionFailed**: Transitions the auction state to `Failed`.
- **isSenderContract**: Checks if the sender is a contract.

## Events

- **DepositorRegistered**: Emitted when a new depositor is registered.
- **Deposit**: Emitted when a deposit is made.
- **Withdraw**: Emitted when a withdrawal is made.
- **Slash**: Emitted when a deposit is slashed.
- **BidSubmitted**: Emitted when a bid is submitted.
- **AddressWhitelisted**: Emitted when an address is whitelisted.
- **AuctionDeployed**: Emitted when the auction is deployed.
- **AuctionStarted**: Emitted when the auction starts.
- **AuctionDepositPending**: Emitted when the auction transitions to `DepositPending`.
- **AuctionEnded**: Emitted when the auction ends.
- **AuctionFailed**: Emitted when the auction fails.


## Abstractions

There are two abstractions:
 - ValidatorAuction: this is the default abstraction, using the values of the enum as predicates.
 - ValidatorAuction+EPA: this is the default abstraction, using the EPA predicate abstraction