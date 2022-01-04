# A Poker Game Smart Contract

### Assumptions:
A. My Poker Game contract is single player, a Player vs the Dealer which is an automated opponent mapped to your address.

Other Information:
1. I built a Frontend to integrate with the smart contract so you can see the contract/integration working fine.
2. The generatePlayerHand function is expensive to call so I plan to remove it and use chainlink keepers to call it from a server.
3. The Frontend is interacting with the master branch, but the generatePlayerHand Function is in the ``generate-hand`` branch.
4. I have removed a function named determineWinner which initially ran a bunch of algorithms to see what type of hand the player/dealer had and then determine the winner.

Github Repos:
Frontend / Game: https://github.com/davien21/poker
Live at: https://poker-davien21.vercel.app/

### Gameflow:

1. A player first calls the function to approve an amount of money to bet or play the game with.
2. This initialises the amount in both the player and dealer’s pockets to the approved amount.
3. The player plays a series of rounds by calling a function on the smart contract which generates a set of cards for both the player and dealer.
4. Details of the current state of the game are saved each round and mapped to the player’s address.
5. The game ends when either the player or dealer’s balance hits 0.

### Edgecases:

There were none, but here’s a couple of issues I ran into:
High gas fees due to the expensive algorithms to generate the cards.
I had to migrate the code to determine the winner of each round to the frontend.
I could have used Chainlink to call this function from a server, but it seemed redundant so I moved it to the frontend I made.
