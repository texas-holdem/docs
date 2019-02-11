# Texas Hold'em Basics

## Overview



### Goals

1. Define a set of functions for texas hold’em game and analysis.

### Non-Goals

1. Implementation details.



## Model

See [base.proto](https://github.com/texas-holdem/tcl/blob/master/proto/base.proto)

## API

#### `CreateTable(n int) : void`

* `n` number of seats of the table.

Creates a new table with `n` seats.  
Seat id will be `[0, n - 1]`.

#### `AddPlayer(seatId int) : void`

* `seatId` the seat id the player will sit.

Adds a player at given seat id.

#### `RemovePlayer(seatId int) : void`

* `seatId` the seat id of the player to be removed from.

Removes the player at given seat id.

#### `StartGame() : void`
Starts the game, will be used to initialze stats for the whole game.

#### `StartRound() : Bet[]`

* `$return` Initial bets of each player.

Starts a new round.  
Returns the initial bets of each player, i.e. small blind, big blind and ante(if any).

#### `PlayerRaise(seatId int, amount int) : void`

* `seatId` seat id of the player who raises.
* `amount` number of chips this player bets.

Player raises with a certain amount of money.

#### `PlayerFold(seatId int) : void`

* `seatId` seat id of the player who folds.

Player folds his hand.

#### `DealCardsToPlayers() : Card[][]`

* `$return` cards dealt to each player.

Deals cards to each player.  
`$return`'s length will be `n`, which is the table size.  
`$return[i]` means the cards dealt to seat `i`, which will be a length-2 array if this seat has player, or a length-0 array if this seat is empty.

#### `DealFlopCards() : Card[]`

* `$return` flop cards.

Deals flop cards.
`$return` will have exactly 3 cards.

#### `DealTurnCard() : Card`

* `$return` turn card.

Deals turn card.

#### `DealRiverCard() : Card`

* `$return` river card.

Deals river card.

#### `ComputeScores() : Score[]`

* `$return` scores of each player.

Compute the scores of each player.  
`$return`'s length will be `n`, which is the table size.

#### `ComputeChips() : int[]`

* `$return` number of chips that each player wins.

Compute the number of chips that each player wins.  
`$return`'s length will be `n`, which is the table size.  
Usually there will be only one positive int in the array. When there's a tie or split, there might be multiple positive ints.
