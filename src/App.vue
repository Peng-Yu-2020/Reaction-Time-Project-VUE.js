<template>
<div>
  <h1>Peng Reaction Timer</h1>
  <button @click="start">play</button>
</div>
 
</template>

<script>


export default {
  name: 'App',
  components: {},
  data(){
    return {
      isplaying: false,
      delay: null,
    }
  },
  methods: {
    start(){
      this.isplaying=true
      this.delay = 2000+Math.random()*5000
      
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
