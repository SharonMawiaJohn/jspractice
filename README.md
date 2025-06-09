# jspractice
Practice purposes only.
I am oing through the js MDN documentation.
The instructions are 

*** I want you to create a simple "guess the number" type game. It should choose a random number between 1 and 100, then challenge the player to guess the number in 10 turns. After each turn, the player should be told if they are right or wrong, and if they are wrong, whether the guess was too low or too high. It should also tell the player what numbers they previously guessed. The game will end once the player guesses correctly, or once they run out of turns. When the game ends, the player should be given an option to start playing again. ***

And I am expected to think like a developer and here are the steps that I will take so as to solve it successfully.

Step 1. Generate a random number between 1 and 100.

Step 2. Record the turn number the player is on. Start it on 1.

Provide the player with a way to guess what the number is.

Once a guess has been submitted first record it somewhere so the user can see their previous guesses.

Next, check whether it is the correct number.

If it is correct:

Display congratulations message.
Stop the player from being able to enter more guesses (this would mess the game up).
Display control allowing the player to restart the game.
If it is wrong and the player has turns left:

Tell the player they are wrong and whether their guess was too high or too low.
Allow them to enter another guess.
Increment the turn number by 1.
If it is wrong and the player has no turns left:

Tell the player it is game over.
Stop the player from being able to enter more guesses (this would mess the game up).
Display control allowing the player to restart the game.
Once the game restarts, make sure the game logic and UI are completely reset, then go back to step 1.

Explaining the first bit of the code.
Line 1 — Generate a random number between 1 and 100:
js
Copy
Edit
let randomNumber = Math.floor(Math.random() * 100) + 1;
What's happening:

Math.random() → gives a random number between 0 and 1 (like 0.726).

Math.random() * 100 → scales it up to a number between 0 and 99.999.

Math.floor(...) → removes the decimal part, so you get 0 to 99.

+ 1 → shifts it to 1 to 100.

✅ So this line is saying:
“Pick a whole number between 1 and 100 and store it in randomNumber.”

🎯 Lines 2–4 — Grab HTML elements for display:
js
Copy
Edit
const guesses = document.querySelector(".guesses");
const lastResult = document.querySelector(".lastResult");
const lowOrHi = document.querySelector(".lowOrHi");
What they do:

These lines grab elements from the HTML using document.querySelector(...). You're storing them in variables so JavaScript can change them later (like adding text, colors, etc.).

.guesses → a place to show all guesses made.

.lastResult → a place to show if the last guess was right or wrong.

.lowOrHi → a place to say whether the guess was too low or too high.

✅ These are references to parts of your web page that will be updated when the user guesses.

🔘 Lines 5–6 — Get the input and submit button:
js
Copy
Edit
const guessSubmit = document.querySelector(".guessSubmit");
const guessField = document.querySelector(".guessField");
guessField is the input box where the user types a number.

guessSubmit is the button they click to make a guess.

You’ll add an event listener later to respond when that button is clicked.

🔢 Line 7 — Track number of guesses:
js
Copy
Edit
let guessCount = 1;
Keeps track of how many guesses the user has made.

Starts at 1, and you'll increment it after each guess.

✅ Useful for ending the game after a certain number of tries (like 10).

🔁 Line 8 — Placeholder for the reset button:
js
Copy
Edit
let resetButton;
This is just declaring a variable.

You’ll use it later when the game is over to let the user restart.

It's declared up front so it's available in a wider scope (i.e., accessible in multiple parts of your script).