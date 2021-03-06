---
module: fundamentals

level: 1

methods:
  - team
  - pair
  - solo

tags:
  - wip
---

# Rock Paper Scissors

<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a>

> This is part of Academy's [technical curriculum for **The Mark**](https://github.com/WeAreAcademy/curriculum-mark). All parts of that curriculum, including this project, are licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.

You have learned how to build a **Command Line Interface** (CLI) game in Python. This means that you can also learn how to build a CLI in **JavaScript**!

In this challenge, you will work out how an existing CLI game in JavaScript works, using the same ideas which you've been applying in Python: _variables_, _control flow_ and _functions_.

As an extension, you will then try to extend the game by adding in some further behaviour.

## Learning Outcomes

- Interpret code written by others
- Use variable declaration and assignment in JavaScript
- Use control flow in JavaScript
- Use functions and arguments in JavaScript
- Use search engines as a learning and knowledge aid
- Add code to a codebase written by others

## Exercise 1: Installing and demoing

**Success criterion:** playing a few games of Rock Paper Scissors on your local machine by running the JavaScript programme written.

Firstly, clone this repository to your local machine in some sensible place, for example:

```bash
cd ~/Development/Academy # or wherever you're organising everything
git clone git@github.com:WeAreAcademy/mark-fundamentals-proj--js-rock-paper-scissors.git
```

Then, change into the new directory and install the files:

```bash
cd mark-fundamentals-proj--js-rock-paper-scissors
yarn
```

Finally, run the programme!

```bash
yarn start
```

### Some installation notes of interest

1. `yarn start` is using the `start` script specified in `package.json` - just as you can run Python files with `python path/to/script.py`, you can run JavaScript files with `node path/to/script.js`.
2. `jest` is listed under `devDependencies`, with `readline-sync` under `dependencies` - but both get installed when you run `yarn`. You can [read a bit about the difference in the NPM docs](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file).

## Exercise 2: Reading, understanding and documenting

**Success criterion:** a document which outlines how you think this JavaScript programme works. You don't have to achieve a theory which explains 100%, but you should strive to explain as much as possible.

(N.B.: The _correctness_ of your theory is **much less important** than the _process_ of forming this document. [Forming a prediction, and then discovering it was wrong, is an effective way to learn](https://www.sciencedirect.com/science/article/abs/pii/S0959475217303468)!)

As a _learning exercise_ in reading and thinking about code, here are some steps that we _suggest_ (not as a strict sequential ordering):

### a) Take some time to read and digest the code.

You should look through both the main code (`src/rock-paper-scissors.js`) as well as the test code (`src/rock-paper-scissors.test.js`) - as well as helping check functionality, tests also serve as documentation of a codebase and how things are meant to work.

(Notice that there isn't 100% test coverage - not all functions have tests written for them. This isn't uncommon in an actual codebase - most teams don't follow perfectly strict test-driven development.)

### b) Add comments for the parts you understand.

At this point in time, you're trying to make sense of the code, and hold a lot of things together in your head.

It will help your learning to take some of those things out of your head and put them down in writing, so we suggest that you begin documenting your understanding of the code by adding comments that explain what is happening.

For example, here is how you might try to document your understanding of a line of code within a function:

```js
function printGreeting(name) {
  /**
   * I think console.log is printing
   *  out the message we pass to it.
   *  This message comes from joining
   *  together three parts into a single
   *  combined message.
   */
  console.log("Hi there, " + name + "!");
}
```

... but you have the freedom to document in whatever way seems helpful or sensible to you.

(Unsure of the syntax for adding comments in JavaScript? Google it!)

_(N.B. This documenting exercise is suggested as a learning tool rather than a production codebase best practice.)_

### c) Google things you don't understand.

We expect that there are things in the code which you won't immediately fathom (e.g. `Object.values`).

Google them and see if you can make sense of them!

### d) Experiment with changing things.

A great way to test your understanding of things is to experiment, change things, and see what breaks.

Things you might try doing:

- You have a theory about a variable - try doing a `console.log` of it to get some _visibility_ on its value
- You have a theory about the flow of a function - try moving things around inside it and see whether it breaks as you expect

### e) Produce a narrative document.

One way you could do this would be to explain a few different games of Rock Paper Scissors.

A good narrative document for this game would walk through a few different games of Rock Paper Scissors and explain how the programme code is leading to the terminal output. (Screenshots of the terminal and/or snippets of programme code are likely to be helpful here.)

Things that you should try to include (amongst other things):

- How is it determined who wins out of the player or the computer?
- What is the apparent role or purpose of the 'variants'?
- What does `Math.floor(Math.random() * 3)` do and how does it help?
- Why is there a `while` loop in `getUserChoice()`?

## Exercise 4: Check your understanding

**Success criterion:** a conversation with a Faculty member and amended comments.

Talk to a member of Faculty about your understanding of the game.

Amend the comments on your copy of the code for any important points that come out of the conversation.

## Exercise 5: Extend the game

**Success criterion:** a game which can be playtested and which satisfies the specified requirements for each extension.

We suggest you also use this as an opportunity to practice writing more tests!

### Extension 1 (important): Rock Paper Scissors Lizard Spock

Rock Paper Scissors often ends in draws - something which some people think is a feature, and others think is a bug!

Let's assume that reducing the likelihood of draws is desirable, and extend the game to [_Rock Paper Scissors Lizard Spock_](http://www.samkass.com/theories/RPSSL.html).

(How to play? Check out [Sheldon Cooper's explanation](https://www.youtube.com/watch?v=Kov2G0GouBw).)

**Requirements**

1. The computer should randomly choose one of the five options
2. All five options (and tolerable variants) should be allowed as input from the user
3. The programme should correctly report back the result of a match

<details>
  <summary>Hints</summary>
  <ul>
    <li>`isWiningChoice` and `acceptableVariants` will need attention</li>
    <li>The trickiest thing is probably now that a single choice has multiple weaknesses...</li>
    <li>... but you might take inspiration from `acceptableVariants` and some code in `asStandardChoice`</li>
  </ul>
</details>

### Extension 2 (less important): replay in a case of draw

When you get a draw in RPS(cLSp), you often immediately replay the game.

Currently, our programme doesn't do that!

**Requirements**

Add a feature where:

1. If you draw, you are asked to play again (until there is an eventual winner)
2. When there is a winner, the programme ends

## Exercise 6: Commentary and reflection

**Success criterion:** documented reflections.

1. What are the main similarities and differences you can see between Python and JavaScript?
2. How easy or difficult was it to understand the code?
   1. What was easiest to understand? In what way?
   2. What was hardest to understand? In what way?
3. How easy or difficult was it to _add to_ the code?
