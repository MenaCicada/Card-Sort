# Card-Sort
idk this was one of my "Intro to Java" assignments and i'm bored so now it's in javascript
```javascript
const card = (name, suit) => {
	return {
		name: String(name),
		suit: String(suit)
	}
}

let deck = []

// Lists possible values. Makes checking and testing faster.
const values = ["2", "3", "4", "5", "6", "7", "8", "9", "Jack", "Queen", "King", "Ace"]
const suits = ["Diamonds", "Clubs", "Hearts", "Spades"]

// Generate cards for testing.
for (let i=0; i<20; i++) {
	deck.push(
		card(
			values[Math.floor(Math.random() * values.length)],
			suits[Math.floor(Math.random() * suits.length)]
		)
	)
}



// Sorting time!
// First, we convert the cards into numbers
let deckValues = []
for (let i=0; i<deck.length; i++) {
	deckValues.push(
		(4 * (values.indexOf(deck[i].name))) +
		(suits.indexOf(deck[i].suit))
	)
}

// Then we sort the numbers from lowest to highest.
for (let i=0; i<deck.length-1; i++) {
	for (let o=0; o<deck.length-1; o++) {
		if (deckValues[o] > deckValues[o+1]) {
			let temp = deckValues[o];
			deckValues[o] = deckValues[o+1]
			deckValues[o+1] = temp
		}
	}
}

// Finally, we convert the result back into cards.
deck = []
for (let cardValue of deckValues) {
	deck.push(
		card(
			values[(cardValue-(cardValue%4))/4],
			suits[cardValue%4]
		)
	)
}

console.log(deck)
alert(JSON.stringify(deck))
```


## Baby Words
1. First we convert each card into a unique number.
    - We want all the 10s to be bigger than all of the 9s
    - If two cards are the same, we sort by suit.
    
    To actually sort by value and suit, we did the following:
    * Multiply the value by 4
    * Convert the suit into a number 0-3
    * Add the two together.
    
2. We sort the numbers from lowest to highest.
    - Each card will slowly move to their sorted position, 1 step at a time.
    
3. Convert numbers back into cards.
    - Get the value of a card by doing `(cardValue-(cardValue%4)/4)`
    - Get the suit of a card by doing `(cardValue%4)`
