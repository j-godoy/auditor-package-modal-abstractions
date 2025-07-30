# SimpleAuction Smart Contract

The `SimpleAuction` contract is a basic implementation of an auction on the Ethereum blockchain. The contract ensures that bids are only accepted during the auction period.
Bids that are not the highest are stored in a `pendingReturns` mapping, allowing users to withdraw their bids safely.

## Contract Details
- **Auction Start**: The auction starts when the contract is deployed.
- **Bidding Time**: The auction lasts for a predefined period (in seconds).


### State Variables

- `auctionStart`: The timestamp when the auction starts.
- `biddingTime`: The duration of the auction in seconds.
- `highestBidder`: The address of the highest bidder.
- `highestBid`: The highest bid amount.
- `pendingReturns`: A mapping of addresses to bid amounts for withdrawals.
- `ended`: A boolean indicating whether the auction has ended.

### Events

- `HighestBidIncreased(address bidder, uint amount)`: Emitted when a new highest bid is received.
- `AuctionEnded(address winner, uint amount)`: Emitted when the auction ends.

### Functions

- `constructor()`: Initializes the auction with the beneficiary address and sets the auction start time and bidding duration.
- `bid()`: Allows users to place bids. The bid must be higher than the current highest bid. If the bid is not higher, the transaction is reverted.
- `withdraw()`: Allows users to withdraw their bids if they have been outbid.
- `auctionEndTime()`: Returns the timestamp when the auction will end.
- `auctionEnd()`: Ends the auction and transfers the highest bid to the beneficiary.

## Usage

1. **Deploy the Contract**: Deploy the contract to the Ethereum network.
2. **Place Bids**: Users can place bids by calling the `bid` function and sending Ether.
3. **Withdraw Bids**: Users who have been outbid can withdraw their bids by calling the `withdraw` function.
4. **End the Auction**: Once the auction duration has passed, the `auctionEnd` function can be called to end the auction and transfer the highest bid to the beneficiary.


## Abstractions

There are three abstractions:
 - SimpleAuction+EPA: this is the default abstraction, using the EPA predicate abstraction.
 - SimpleAuction+EPA+Ended: this is the abstraction using the EPA predicate abstraction, plus a predicate `Ended`.
 - SimpleAuction+Ended+highestBidder: this is the abstraction using a predicate `Ended`, plus a predicate `highestBidder`.