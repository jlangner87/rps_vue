# Vue Rock, Paper, Scissor

![](https://res.cloudinary.com/practicaldev/image/fetch/s--RgTOJxWn--/c_imagga_scale,f_auto,fl_progressive,h_720,q_auto,w_1280/https://thepracticaldev.s3.amazonaws.com/i/d440mmj72v2vi7ad76ir.png)

## Getting Started

- Fork and Clone
- `npm install`
- `npm run serve`

## Overview

In this lab, you'll be building a Rock, Paper, Scissor game using VueJS. You'll utilize your new knowledge of `state`, `methods`, and `directives` to build a functioning game.

## Directions

### Step 1

Start by importing the `choices` array into your App.vue from the `choices.js` file.

Create `4` pieces of state by following the below table:

| state         | value                                    |
| ------------- | ---------------------------------------- |
| playerChoices | choices (the array you imported earlier) |
| playerChoice  | null                                     |
| compChoice    | null                                     |
| winner        | string                                   |

### Step 2

Define `3` methods:

- selectChoice
  - accepts an argument of `value` which will be used to set the playersChoice
- checkWinner
- resetGame

### Step 3

Utilizing the `choices` state, create a button with the `v-for` directive in the div with the `buttons` class.

This button should have the following properties:

- :disabled => set this to playerChoice
- class="flex-item"
- :key => choice id
- @click => selectChoice => make sure to pass the `choice` from the `v-for` as an argument

Inside of the button, add an `img` with a `src` of each choices image.

Below the image, add a `h4` with the content of `choice.label`.

You should have the following structure when you're done:

```jsx
<div class="flex-row buttons">
  <button>
    <img />
    <h4></h4>
  </button>
</div>
```

### Step 4

Implement your `selectChoice` method. You should:

- set the provided value as the playerChoice
- set compChoice to a random choice from the `playerChoices`

**You'll implement the final part (checkWinner) later on.**

Check your work with the Vue Devtools to ensure that the `playerChoice` and `compChoice` are getting set to state.

### Step 5

Next we'll set up our `checkWinner` function. This function should compare the `playerChoice` to the `compChoice`.

- if the player choice is the same as the computer choice, set the winner to `It's a draw!`.
- if the player wins, set the winner to `Player Won!`
- if the computer wins, set the winner to `Computer Won!`

Once you've completed the `checkWinner` function, invoke this function in `selectChoice`: `this.checkWinner()`

### Step 6

Create a new method called `resetGame` that resets all of the state back to it's initial value

### Step 7

Next we'll display the choices and the winner.

Below the div with the `buttons` class, create a new div with the following classes:

- winner-circle
- flex-row

This div should have a `v-if` directive that checks for the winner state.

In this div:

- create a div with the class `flex-item`. It should contain the following:
  - h4 with the text `Player Chose`
  - `img` with the `src` being set to the `playerChoice` image property.
- the second div you'll create within the `winner-circle`, will contain the current winner and a button that is clicked to reset the game.
- The last and final div will contain:
  - a class of `flex-item`
  - h4 with the text `Computer Chose`
  - `img` with a `src` being set to the `compChoice` image property

Your final structure should look like the following

```jsx
<div class="winner-circle flex-row">
  <div class="flex-item"></div>
  <div></div>
  <div class="flex-item"></div>
</div>
```

## Resources

- [Vue Directives](https://012.vuejs.org/guide/directives.html)
- [Vue State](https://vuejs.org/v2/guide/state-management.html)
