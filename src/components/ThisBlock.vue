<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default {
    props: ["delay"],
    mounted(){
      setTimeout(()=>{
        this.showBlock=true
        this.startTimer()
      }, this.delay)
    },
    updated(){
      console.log("updated!")
    },
    unmounted(){
      console.log("unmounted")
    },
    data(){
      return {
        showBlock: false,
        reactionTime: 0,
        timer: null,
      }
    },
    methods: {
      startTimer(){
        this.timer = setInterval(() => {
          this.reactionTime += 10
        }, 10)
      },
      stopTimer(){
        clearInterval(this.timer)
        this.showBlock = false
        this.$emit("end", this.reactionTime)
        console.log(this.reactionTime)
      }
    }
}
</script>

<style>
    .block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>