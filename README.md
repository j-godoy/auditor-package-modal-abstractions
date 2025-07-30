# General Comments

This folder contains eight Solidity smart contracts:
- Auction
- Crowdfunding
- EPXCrowdsale
- EscrowVault
- RefundEscrow
- RockPaperScissors
- SimpleAuction
- ValidatorAuction

Each subject includes:
- `.sol`: Contains the Solidity smart contract source code. If there are multiple `.sol` files, it is due to minor fixes. The fixed version includes 'Fix' in the file name.
- `.svg`: Diagram of the generated abstraction, one for each abstraction.
- `.dot`: Editable version of the `.svg` file.
- `README`: Provides an overview of the smart contract and briefly explains which abstractions (`.svg`/`.dot` files) are included and which predicates were used to generate them.

### Note 1

The abstractions contain only public, non-view functions as transitions. For example, internal functions will not appear in the abstraction.

### Note 2

An abstraction named the same as the Solidity file represents a default abstraction, generated using enum fields in the code as predicates. For example, if the code contains an enum `state` with values `open`, `closed`, and `failed`, the predicates used are `state=open`, `state=closed`, and `state=failed`.

An abstraction named the same as the Solidity file with a suffix `+EPA` represents a default abstraction, generated using the preconditions of the public non-view functions as predicates.

An abstraction named the same as the Solidity file with a suffix `+X` indicates that the `X` predicate was used to generate the abstraction.

