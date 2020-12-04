<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :delay="delay" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="this.delay" @end="endGame" />
    <Results v-if="isResults" :result="this.score" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      isResults: false,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000
      this.isPlaying = true
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.isResults = true
    },
  },
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
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 1em;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
