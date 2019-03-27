# Hangman-Project-Board
Week 3 Homework
1. Pick a random word.
2. Take the player’s guess.
3. Quit the game if the player wants to.
4. Check that the player’s guess is a valid letter.
5. Keep track of letters the player has guessed.
6. Show the player their progress.
7. Finish when the player has guessed the word.

Pseudocode:
Pick a random word
While the word has not been guessed {
 Show the player their current progress
 Get a guess from the player
 If the player wants to quit the game {
 Quit the game
 }
 Else If the guess is not a single letter {
 Tell the player to pick a single letter
 }
 Else {
 If the guess is in the word {
 Update the player's progress with the guess
 }
 }
}
Congratulate the player on guessing the word

The answer array will start out as a group of these empty
entries equal in number to the letters in the secret word. For
example, if the secret word is fish, the array would look like this:
["_", "_", "_", "_"]
If the player correctly guessed the letter i, we’d change the second blank to an i:
["_", "i", "_", "_"]
Once the player guesses all the correct letters, the completed
array would look like this:
["f", "i", "s", "h"]

Game Loop:
1. Takes input from the player
2. Updates the game state
3. Displays the current state of the game to the player

Choosing a random word:
We begin our game at u by creating an array of words
(javascript, monkey, amazing, and pancake) to be used as the
source of our secret word, and we save the array in the words
variable. The words should be all lowercase. At v we use
Math.random and Math.floor to pick a random word from the array.

Creating the Answer Array:
Next we create an empty array called answerArray and fill it with
underscores (_) to match the number of letters in the word.
var answerArray = [];
u for (var i = 0; i < word.length; i++) {
 answerArray[i] = "_";
}
var remainingLetters = word.length;
The for loop at u creates a looping variable i that starts at 0
and goes up to (but does not include) word.length. Each time around
the loop, we add a new element to answerArray, at answerArray[i].
When the loop finishes, answerArray will be the same length as word.
For example, if word is "monkey" (which has six letters), answerArray
will be ["_", "_", "_", "_", "_", "_"] (six underscores).
Finally, we create the variable remainingLetters and set it to
the length of the secret word. We’ll use this variable to keep track
of how many letters are left to be guessed. Every time the player
guesses a correct letter, this value will be decremented (reduced)
by 1 for each instance of that letter in the word.
