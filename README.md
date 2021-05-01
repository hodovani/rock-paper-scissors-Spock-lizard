# rock-paper-scissors-Spock-lizard

Welcome to my tutorial!

In this tutorial, we're gonna build a really simple game of Rock Paper Scissors Spock Lizard.

Please check my GitHub account for the complete source code.
https://github.com/hodovani/rock-paper-scissors-Spock-lizard

We are gonna use vanilla JavaScript, HTML, CSS for this game.

YouTube video
https://youtu.be/pJw39quoajE

Let's get started.

First, we need to set up our project folder.

Please create a folder for the game.

Put an empty `index.html`, `index.css`, `index.js` file in the folder.


Now you want to put some tags in `index.html`.

```html
<html>
  <head>
    <title>GAME</title>
  </head>
  <body>
  </body>
</html>
```

Don't forget to save the file periodically.

We can check that we doing fine by running this file in a browser.

Okay, We can move forward.

Now you want to add input elements for a user.

```html
<span>YOUR CHOICE</span>
    <div id="user-options">
        <div>
            <input type="radio" id="1" name="option" class="user-option">
            <label for="1">⛰️</label>
        </div>
        <div>
            <input type="radio" id="2" name="option" class="user-option">
            <label for="2">✂️</label>
        </div>
        <div>
            <input type="radio" id="3" name="option" class="user-option">
            <label for="3">🧻</label>
        </div>
        <div>
            <input type="radio" id="4" name="option" class="user-option">
            <label for="4">🖖</label>
        </div>
        <div>
            <input type="radio" id="5" name="option" class="user-option">
            <label for="5">🦎</label>
        </div>
    </div>
```

We want to add it at the end of `index.html` body tag.

Looks good to me!

We need to add computer output, game result, button to play the game.

The computer output should look next:

```html
<span>COMPUTER CHOICE</span>
<div id="computer-choice">💭</div>
```
You want to add it at the end of your `index.html` body tag.

The play button is pretty simple:

```html
<button id="play">▶️</button>
```
You want to add it at the end of your `index.html` body tag.

The game result should look next:

```html
<div id="output"></div>
```

You want to add it at the end of your `index.html` body tag.

Now you want to link your `index.css` and `index.html` files.

Please add 

```html
<script type="text/javascript" src="./index.js"></script>
```

at the bottom of the body.

That's it. We finished our work with `index.html`.

We just want to increase the font size to make emojis look better.

You want to add this to your index.css:

```CSS
html {
    font-size: 42px
}
```

Let's flip over to our JavaScript file.

We need a function to return a random number in range 1 to 5 for a computer choice.

We would name it `getComputerChoice` and it should look like this one:

```javascript
function getComputerChoice() {
    return Math.floor((Math.random() * 5) + 1);
}
```

Put it at the beginning of the `index.js` file.

We want to add some consts that would help us later. Just put it at the end of your `index.js`

```
const ROCK = 'ROCK';
const SCISSORS = 'SCISSORS';
const PAPER = 'PAPER';
const SPOCK = 'SPOCK';
const LIZARD = 'LIZARD';
const OPTIONS = {
    1: ROCK,
    2: SCISSORS,
    3: PAPER,
    4: SPOCK,
    5: LIZARD
};
const OPTIONS2EMOJI = {
    1: '⛰️',
    2: '✂️',
    3: '🧻',
    4: '🖖',
    5: '🦎'
};
```

Now we want to store user input somewhere. Let's add a variable for that.

```
let userChoiceID = '';
```

We want to add event listeners for user input when a page is loaded. 

To do that we should write our code inside the callback function.

```javascript
window.onload = () => {
  // your code here
}
```

We want to put it at the end of `index.js`.

We need an element to output results. 

```
const output = document.querySelector('#output');
```

Put it at the beginning of `onload` function.

We want to add event listeners to handle user input. First, we would select elements by class. Then we would add an event listener to each element. 

```
const userOptions = document.querySelectorAll('.user-option');

userOptions.forEach(el => el.addEventListener('click', event => {
    userChoiceID = event.target.id;
}));
```

Put it at the end of `onload` function.


Now we want to add an event listener to the play button. Let's create a variable for it first.

```
const playButton = document.querySelector('#play');
```

We can now add an event listener

```
playButton.addEventListener('click', () => {
})
```

Let's collect all the information that we need to determine the winner. We need a computer and user choice. 

```
const computerChoiceID = getComputerChoice();
const computerChoice = OPTIONS[computerChoiceID];
const computerChoiceElement = document.querySelector('#computer-choice');
const output = document.querySelector('#output');
const userChoice = OPTIONS[userChoiceID];

let result = '';
```

Now we can output computer choice.

```
computerChoiceElement.innerHTML = OPTIONS2EMOJI[computerChoiceID];
```

Put it at the end of the play button click callback.

Let's write logic to determine a winner. We would use a switch for that. Don't forget to add a default case.

```
switch (`${computerChoice}-${userChoice}`) {
    case `${ROCK}-${ROCK}`:
    case `${SCISSORS}-${SCISSORS}`:
    case `${PAPER}-${PAPER}`:
    case `${SPOCK}-${SPOCK}`:
    case `${LIZARD}-${LIZARD}`:
        result = 'TIE 👔'
        break;
    case `${ROCK}-${SCISSORS}`:
    case `${ROCK}-${LIZARD}`:
    case `${SCISSORS}-${PAPER}`:
    case `${SCISSORS}-${LIZARD}`:
    case `${PAPER}-${ROCK}`:
    case `${PAPER}-${SPOCK}`:
    case `${SPOCK}-${ROCK}`:
    case `${SPOCK}-${SCISSORS}`:
    case `${LIZARD}-${PAPER}`:
    case `${LIZARD}-${SPOCK}`:
        result = 'COMPUTER WIN 😔💔 🤖🥇'
        break;
    case `${ROCK}-${PAPER}`:
    case `${ROCK}-${SPOCK}`:
    case `${SCISSORS}-${ROCK}`:
    case `${SCISSORS}-${SPOCK}`:
    case `${PAPER}-${SCISSORS}`:
    case `${PAPER}-${LIZARD}`:
    case `${SPOCK}-${PAPER}`:
    case `${SPOCK}-${LIZARD}`:
    case `${LIZARD}-${ROCK}`:
    case `${LIZARD}-${SCISSORS}`:
        result = 'YOU WIN ☺️🥇 🤖💔'
        break;
    default:
        result = 'SOMETHING WRONG. TRY AGAIN. 🐛'
}
```

Put it at the end of the play button click callback.

Now we are ready to output the result.

```
output.innerHTML = result;
```

Put it at the end of the play button click callback.

There you have it you can now play against the computer.

There are plenty of cool ways to improve on this simple pure JavaScript rock-paper-scissors-Spock-lizard including a score count

Once again I hope you enjoyed my tutorial if you have any questions regarding the code please leave a comment.

I'll make sure to get back to you with help.
