<script>
import Block from './components/Block.vue'
import Result from './components/Results.vue'

export default{
  components: {Block, Result},
  data()
  {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods:
  {
    startGame()
    {
      this.showResult = false
      this.delay = 2000 + Math.random() * 5000
      this.score = null
      this.isPlaying = true
    },
    endGame(reactionTime)
    {
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    },
  }

}

</script> 

<template>
  <h1>Reaction Time Games!</h1>
  <button @click="startGame" :disabled="isPlaying" class="playBtn">
    <span v-if="isPlaying">Playing...</span>
    <span v-else>Start Game</span>
  </button>
  <Result :score="score" v-if="showResult"/>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<style>
*
{
  margin: 0;
  padding: 0;
  font-family: Poppins;
}
#app
{
  margin-top: 60px;
  text-align: center;
  color: #444;
}
.playBtn
{
  cursor: pointer;
  margin-top: 12px;
  padding: 7px;
  border: none;
  border-radius: 8px;
  color: #fff;
  background-color: #20caa5;
}
.playBtn:hover
{
  background-color: #1eaf90;
}
.playBtn[disabled]
{ 
  opacity: 0.7;
  cursor: not-allowed;
}
</style>
