# RefundEscrow Smart Contract

## Overview

The `RefundEscrow` contract is an escrow mechanism designed to hold funds for a beneficiary, deposited from multiple parties. It allows for the management of these funds, enabling either withdrawal by the beneficiary or refunds to the depositors based on the state of the escrow.

## Contract Details

### States

The contract operates in three states:
- `Active`: The escrow is open for deposits.
- `Refunding`: Deposits are being refunded to the depositors.
- `Closed`: The deposit period is closed, and the beneficiary can withdraw the funds.

### Events

- `RefundsClosed()`: Emitted when the escrow is closed for deposits and the beneficiary can withdraw the funds.
- `RefundsEnabled()`: Emitted when the escrow is set to refunding state, allowing depositors to withdraw their funds.

### Constructor

The constructor initializes the contract with the beneficiary's address and sets the initial state to `Active`.


## Abstractions

There are two abstractions:
 - RefundEscrow: this is the default abstraction, using the values of the enum as predicates.
 - RefundEscrow+EPA: this is the default abstraction, using the EPA predicate abstraction.