<template>
  <h1>Clicky Clicky</h1>
  <button @click="start" :disabled="gameStarted">Play</button>
  <p>See how fast your reaction time is ? </p>
  <Block v-if="gameStarted" :delayTimer="delayTimer" @endOfGame="endOfGame"/>
  <Results :score="score" v-if="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      gameStarted: false,
      delayTimer: null,
      score: null
    }
  },
  methods: {
    start() {
      this.score = null
      this.gameStarted = true
      this.delayTimer = 2000 + Math.random() * 5000
    },
    endOfGame(timeToClick) {
      this.score = timeToClick
      this.gameStarted = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
