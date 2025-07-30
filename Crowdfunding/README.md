# Auction Smart Contract


## Contract Description

This is a simple crowdfunding smart contract written in Solidity. The contract allows users to donate (just once) funds to a project within a specified block limit. If the funding goal is reached by the end of the block limit, the owner can withdraw the funds. If the goal is not reached, backers can claim their donations back.

### State Variables

- `address payable owner`: The owner of the crowdfunding campaign.
- `uint max_block`: The block number until which donations are accepted.
- `uint goal`: The funding goal in wei.
- `mapping(address => uint) backers`: A mapping to track the donations made by each backer.
- `bool funded`: A flag indicating whether the funding goal has been reached.



## Abstractions

There are two abstractions:
 - Crowdfunding_EPA+Balance: This is the abstraction using the EPA predicate + `Balance > 0` predicate.
 - CrowdfundingFix_EPA+Balance: this is the default abstraction, using the EPA predicate abstraction, but over a fixed version. This version changes the precondition of Donate method to `max_block < block.number` instead of `max_block <= block.number`.