<template>
<div>
  <h1>Peng Reaction Timer</h1>
  <button @click="start" :disabled="isplaying">play</button>
  <ThisBlock  v-if="isplaying" :delay='delay' @end="endGame"/>
  <ThisResults v-if="showScore" :score="score" />
</div>
 
</template>

<script>
import ThisBlock from "./components/ThisBlock.vue"
import ThisResults from "./components/ThisResults.vue"


export default {
  name: 'App',
  components: {ThisBlock, ThisResults},
  data(){
    return {
      isplaying: false,
      delay: null,
      score: null,
      showScore: false,
    }
  },
  methods: {
    start(){
      this.isplaying= true
      this.showScore = false
      this.delay = 2000+Math.random()*5000
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.showScore = !this.showScore
      this.isplaying = !this.isplaying
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
button {
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 16px;
    letter-spacing: 1px;
    cursor: pointer;
    margin: 10px;
  }
  button[disabled] {
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
