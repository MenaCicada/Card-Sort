# Card-Sort

## Procedure
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
