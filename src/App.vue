<template>
  <h1> Reaction Speed </h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <HelloWorld v-if="isPlaying" :delay="delay" @end="endGame"/>
  <ResultGame v-if="showResults" :score="score"/>
  <!-- <p v-if="showResults">Reaction Time: {{ score }} ms</p> -->
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ResultGame from './components/ResultGame.vue'

export default {
  name: 'App',
  components: {
    HelloWorld, ResultGame
  },
  data() {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: null
    }
  },
  
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      console.log(this.delay)
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background: coral;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}   
</style>
