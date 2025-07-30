# RockPaperScissors Smart Contract

This Solidity smart contract implements a simple Rock-Paper-Scissors game on the Ethereum blockchain. The contract allows two players to participate in the game, make their choices, and determine the winner based on the traditional rules of Rock-Paper-Scissors.

## Contract Overview

### State Variables

- `address payable player1`: Address of the first player.
- `address payable player2`: Address of the second player.
- `address payable owner`: Address of the contract owner.
- `int p1Choice`: Choice of the first player (initialized to -1).
- `int p2Choice`: Choice of the second player (initialized to -1).
- `uint[3][3] payoffMatrix`: A 2D array representing the payoff matrix for the game.

### Constructor

The constructor initializes the players' addresses and the owner’s address. It also sets up the payoff matrix based on the rules of Rock-Paper-Scissors:

- Rock (0) beats Scissors (2)
- Paper (1) beats Rock (0)
- Scissors (2) beats Paper (1)

### Functions

- `function choicePlayer1(int choice) public`: Allows player 1 to make their choice (0 for Rock, 1 for Paper, 2 for Scissors). The choice can only be made once.
- `function choicePlayer2(int choice) public`: Allows player 2 to make their choice (0 for Rock, 1 for Paper, 2 for Scissors). The choice can only be made once.
- `function determineWinner() public`: Determines the winner based on the choices made by both players. The winner receives the contract's balance. If it's a draw, the owner receives the balance.

### Payoff Matrix

The payoff matrix is defined as follows:
- `payoffMatrix[0][0] = 0`: Rock vs Rock (Draw)
- `payoffMatrix[0][1] = 2`: Rock vs Paper (Player 2 wins)
- `payoffMatrix[0][2] = 1`: Rock vs Scissors (Player 1 wins)
- `payoffMatrix[1][0] = 1`: Paper vs Rock (Player 1 wins)
- `payoffMatrix[1][1] = 0`: Paper vs Paper (Draw)
- `payoffMatrix[1][2] = 2`: Paper vs Scissors (Player 2 wins)
- `payoffMatrix[2][0] = 2`: Scissors vs Rock (Player 2 wins)
- `payoffMatrix[2][1] = 1`: Scissors vs Paper (Player 1 wins)
- `payoffMatrix[2][2] = 0`: Scissors vs Scissors (Draw)



## Abstractions

There are two abstractions:
- **RockPaperScissors+EPA**: This is the default abstraction, utilizing the EPA predicate abstraction.
- **RockPaperScissors+OneWinner**: This abstraction uses a predicate to define the winner (No Betting, Win A, Win B or draw).