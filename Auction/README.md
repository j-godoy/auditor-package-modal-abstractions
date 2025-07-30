# Auction Smart Contract


## Contract Description

The Auction smart contract facilitates a decentralized auction process on the blockchain. It allows users to bid on an item within a specified time frame, ensuring that the highest bidder wins the auction. The contract manages the entire auction lifecycle, from initialization to determining the winner and securely handling funds.

The public functions are `bid`, `withdraw`, and `auctionEnd`. The `bid` function requires that the auction time frame has not ended, and the `value` amount sent must be greater than the current highest bid. The `withdraw` function allows non-winning bidders to retrieve their funds. The `auctionEnd` function requires that the auction time frame has ended and can only be called once.


## Abstractions

There are three abstractions:
 - Auction+EPA: this is the default abstraction, using the EPA predicate abstraction.
 - AuctionTimeFix+EPA: this is the default abstraction, using the EPA predicate abstraction, but over a fixed version (fixed the auctionEnd method).
 - AuctionTimeFix+EPA+Ended: this abstraction uses predicates EPA, plus a predicate `Ended`, over a fixed version (fixed the auctionEnd method).