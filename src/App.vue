<template>
  <h1>game of reaction time</h1>
  <h4>Role of game : click on the play button and after randome time one of box was allowed onder the button. <br> you quackly click on the box and the game say you are faster or weeker</h4>
  <button @click="start" :disabled="isplaying">play</button>
  <div v-if="showreaction">
    <Results :score="score" />
  </div> 
  <Block v-if="isplaying" :delay="delay" @end="endgame" />

</template>

<script>
import Block from '@/components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  data() {
    return {
      delay: null,
      isplaying: false,
      showreaction :false,
      score: null

    }
  },
  components: {
    Block,
    Results
  },
  methods: {
    start() {
      this.delay = 200 + Math.random() * 5000
      this.isplaying = true
      this.showreaction=false


      // console.log(this.delay)
    },
    endgame(reactiontime) {
      this.score = reactiontime
      this.isplaying = false
      this.showreaction=true




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

button{
  background-color: aqua;
  color: white;
  padding: 8px  16px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  margin: 10px;
  letter-spacing: 1px;
  cursor: pointer;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}


</style>
