<template>
  <div id="app">
    <div class="flex-row buttons">
    <button class="flex-item"
    v-for="choice in playerChoices"
    :key="choice.id"
    :disabled="playerChoice"
    @click="selectChoice(choice)"
    >
    <img :src="choice.image"/>
    <h4>{{choice.label}}</h4>
    </button>
    </div>
    <div class="winner-circle flex-row"
    v-if="winner"
    >
      <div>
        <h4>Player Chose {{playerChoice.label}}</h4>
        <img :src="playerChoice.image"/>
      </div>
      <div>
        <h4 v-bind:winner="winner">{{winner}}</h4>
        <button @click="resetGame()">Play Again</button>
      </div>
      <div>
        <h4>Computer Chose {{compChoice.label}}</h4>
        <img class="flex-item" :src="compChoice.image"/>
      </div>
    </div>

  </div>
</template>

<script>
import choices from './choices';
export default {
  name: 'App',
  components: {},
  data: () => ({
    playerChoices: choices,
    playerChoice: null,
    compChoice: null,
    winner: ''
  }),
  methods: {
    selectChoice (value) {
      this.playerChoice=value,
      this.compChoice=Math.floor(((Math.random()*3)+1))
      this.checkWinner()
      this.selectCompChoice() 
      },
    selectCompChoice () {
      if (this.compChoice === 1) {
        let object = choices.find(obj => obj.id ===1)
        this.compChoice=object
      } else if (this.compChoice === 2) {
        let object = choices.find(obj => obj.id ===2)
        this.compChoice=object
      } else if (this.compChoice === 3) {
        let object = choices.find(obj => obj.id ===3)
        this.compChoice=object
      }
    },
    checkWinner () {
      if (this.playerChoice.id === this.compChoice) {
        this.winner="It's a Draw!"
      } else if (this.playerChoice.id === 1 && this.compChoice === 2) {
        this.winner="The Computer Wins!"
      } else if (this.playerChoice.id === 1 && this.compChoice === 3) {
        this.winner="Player Wins!"
      } else if (this.playerChoice.id === 2 && this.compChoice === 3) {
        this.winner="The Computer Wins!"
      } else if (this.playerChoice.id === 2 && this.compChoice === 1) {
        this.winner="Player Wins!"
      } else if (this.playerChoice.id === 3 && this.compChoice === 1) {
        this.winner="The Computer Wins!"
      } else if (this.playerChoice.id === 3 && this.compChoice === 2) {
        this.winner="Player Wins!"
      }
    },
    resetGame () {
     Object.assign(this.$data, this.$options.data.apply(this))
    }
  }
}
</script>

<style>
html {
  background-color: black;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  color: #f4f6f9;
}

.flex-row {
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.flex-item {
  padding: 1em;
  height: 200px;
  width: 200px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  background-color:black;
  border-radius: 100%;
  border: 1px solid rgba(255, 255, 255, 0);
  color: white;
  font-size: 24px;
  margin-bottom: 20px;
}

button {
  border: 0;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:disabled {
  cursor: not-allowed;
}

button:hover:not(:disabled) {
  background: #f4f6f9;
}

.flex-item img {
  width: 205px;
  align-content: center;
  object-fit: contain;
}

.winner-circle {
  margin-top: 8em;
  border: 1px solid rgba(255, 255, 255, 0.2);
  padding: 1em;
  border-radius: 4px;
}

.winner-circle img {
  width: 205px
}

.winner-circle button {
  padding: 1em 2em;
  border-radius: 4px;
  border: 0;
  background-color: #ffcc00;
  font-weight: 700;
}

.winner-circle button:hover {
  border: 0;
}
</style>
