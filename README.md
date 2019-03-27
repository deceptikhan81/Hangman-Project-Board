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
1 for (var i = 0; i < word.length; i++) {
 answerArray[i] = "_";
}
var remainingLetters = word.length;
The for loop at 1 creates a looping variable i that starts at 0
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

Coding the Game Loop:
The skeleton of the game loop looks like this:
while (remainingLetters > 0) {
 // Game code goes here
 // Show the player their progress
 // Take input from the player
 // Update answerArray and remainingLetters for every correct guess
}
We use a while loop, which
will keep looping as long as
remainingLetters > 0 remains true.
The body of the loop will have
to update remainingLetters for every
correct guess the player makes. Once
the player has guessed all the letters,
remainingLetters will be 0 and the loop
will end.

Showing the Player’s Progress:
The first thing we need to do inside the game loop is to show the
player their current progress:
alert(answerArray.join(" "));
We do that by joining the elements of answerArray into a string,
using the space character as the separator, and then using alert
to show that string to the player. For example, let’s say the word
is monkey and the player has guessed m, o, and e so far. The
answer array would look like this ["m", "o", "_", "_", "e", "_"],
and answerArray.join(" ") would be "m o _ _ e _".

Handling the Player’s Input:
Now we have to get a guess from the player and ensure that it’s a
single character.
1 var guess = prompt("Guess a letter, or click Cancel to stop playing.");
2 if (guess === null) {
 break;
3 } else if (guess.length !== 1) {
 alert("Please enter a single letter.");
} else {
4 // Update the game state with the guess
}
At 1, prompt takes a guess from the player and saves it to the
variable guess. One of four things will happen at this point.
JavaScript for Kids
©2015, Nick Morgan 
116 Chapter 7
First, if the player clicks the Cancel button, then guess will be
null. We check for this condition at 2 with if (guess === null). If
this condition is true, we use break to exit the loop.
Note You can use the break keyword in any loop to immediately stop looping, no matter where the program is in the loop or whether the while
condition is currently true.
The second and third possibilities are that the player enters
either nothing or too many letters. If they enter nothing but click
OK, guess will be the empty string "". In this case, guess.length
will be 0. If they enter anything more than one letter, guess.length
will be greater than 1.
At 3, we use else if (guess.length !== 1) to check for these
conditions, ensuring that guess is exactly one letter. If it’s not,
we display an alert saying, “Please enter a single letter.”
The fourth possibility is that the player enters a valid guess of
one letter. Then we have to update the game state with their guess
using the else statement at 4, which we’ll do in the next section.

Updating the Game State:
Once the player has entered a valid guess, we must update the
game’s answerArray according to the guess. To do that, we add the
following code to the else statement:
1 for (var j = 0; j < word.length; j++) {
2 if (word[j] === guess) {
 answerArray[j] = guess;
3 remainingLetters--;
 }
}
At 1, we create a for loop with a new looping variable called j,
which runs from 0 up to word.length. (We’re using j as the variable
in this loop because we already used i in the previous for loop.) We
use this loop to step through each letter of word. For example, let’s
say word is pancake. The first time around this loop, when j is 0,
word[j] will be "p". The next time, word[j] will be "a", then "n", "c",
"a", "k", and finally "e".
At 2, we use if (word[j] === guess) to check whether the current letter we’re looking at matches the player’s guess. If it does,
we use answerArray[j] = guess to update the answer array with
JavaScript for Kids
©2015, Nick Morgan 
Creating a Hangman Game 117
the current guess. For each letter in the word that matches guess,
we update the answer array at the corresponding point. This
works because the looping variable j can be used as an index for
answerArray just as it can be used as an index for word.
For example, imagine we’ve just started playing the game and
we reach the for loop at 1. Let’s say word is "pancake", guess is "a",
and answerArray currently looks like this:
["_", "_", "_", "_", "_", "_", "_"]
The first time around the for loop at 1, j is 0, so word[j]
is "p". Our guess is "a", so we skip the if statement at 2 (because
"p" === "a" is false). The second time around, j is 1, so word[j]
is "a". This is equal to guess, so we enter the if part of the statement. The line answerArray[j] = guess; sets the element at index
1 (the second element) of answerArray to guess, so answerArray now
looks like this:
["_", "a", "_", "_", "_", "_", "_"]
The next two times around the loop, word[j] is "n" and then
"c", which don’t match guess. However, when j reaches 4, word[j]
is "a" again. We update answerArray again, this time setting the
element at index 4 (the fifth element) to guess. Now answerArray
looks like this:
["_", "a", "_", "_", "a", "_", "_"]
The remaining letters don’t match "a", so nothing happens the
last two times around the loop. At the end of this loop, answerArray
will be updated with all the occurrences of guess in word.
JavaScript for Kids
©2015, Nick Morgan 
118 Chapter 7
For every correct guess, in addition to updating answerArray,
we also need to decrement remainingLetters by 1. We do this at 3
using remainingLetters--;. Every time guess matches a letter in word,
remainingLetters decreases by 1. Once the player has guessed all the
letters correctly, remainingLetters will be 0.

Ending the Game
The main game loop condition is remainingLetters > 0, so as long as there are still letters to
guess, the loop will keep looping. Once remainingLetters
reaches 0, we leave the loop. We end with the following code:
alert(answerArray.join(" "));
alert("Good job! The answer was " + word);
The first line uses alert to show the
answer array one last time. The second
line uses alert again to congratulate the
winning player.
