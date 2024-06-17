<template>
    <div class="container">
      <h1>Ninja Reaction Timer</h1>
      <button @click="start" :disabled="isPlaying">Start Game</button>
      <p v-if="isPlaying">Wait for the green block to appear and click on it as fast as you can!</p>
      <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
      <Results v-if="showResults" :reactionTime="score"></Results>
    </div>
</template>

<script>

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block , Results
  },
  data() {
    return {
      isPlaying: false,
      delay : null,
      score : 0,
      showResults : false,
      preClick : false
    }
  },
  methods :{
    start(){
      this.delay = Math.floor(Math.random() * 5000) + 2000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime){
      this.isPlaying = false;
      this.showResults = true;
      this.score = reactionTime;
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
  background-color: #0faf87;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
  font-size: 16px;
  cursor:pointer;
  border: none;
  outline: none;
}

 /* push look of button down */
button:active{
  position:relative;
  top:2px;
}

.container{
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}



</style>
