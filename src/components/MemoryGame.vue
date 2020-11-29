<template>
  <div id="memory_game">
    <h1>Memory Game</h1>
    <div v-if="!isWin">
       <h3>SCORE: {{ score }}</h3>
      <Board id="board" :images="images_array" @match="handleMatch"></Board>
    </div>
    <div v-else>
      <h1>Congratulations!!!</h1>
      <p @click="isWin=resetGame()">Play again</p>
    </div>
   
  </div>
</template>

<script>
import Board from "./Board"
import images from "../images"
export default {
  components: { Board },
  name: 'MemoryGame',
  props: {

  },
  data(){
    return {
      images_array: images,
      score : 0,
      isWin: false
    }
  },
  methods:{
    handleMatch(){
      this.score++
      this.isWin = this.score === this.images_array.length/2
    },
    resetGame(){
      this.isWin = false
      this.score = 0
    }
  },
  mounted(){
    this.images_array.sort(() => 0.5 - Math.random())
  }
}
</script>

<style scoped>
#memory_game, #memory_game > div{
  display:flex;
  justify-content: center;
  flex-direction: column;
}
</style>
