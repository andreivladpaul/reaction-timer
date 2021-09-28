<template>
  <div id="app">
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying"  :delay="delay" @end="endGame"/>
    <Results v-if="showResults" :score="score" />

  </div>
</template>

<script>
import Block from '../src/components/Block.vue'
import Results from '../src/components/Results.vue'


export default {
  name: 'App',
  components: {
    Block, Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true

    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #0660bb;
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  
}
</style>
