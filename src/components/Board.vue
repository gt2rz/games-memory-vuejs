<template>
  <div id="board">
    <Card v-for="(card, id) in images" 
          :key="id" :index="id" 
          :image="card" 
          @flip-card="handleFlipCard"
          ></Card>
  </div>
</template>

<script>
import Card from './Card'

export default {
  name: 'Board',
  components:{
    Card
  },
  props: {
    images:{
      required: true,
      type:Array
    }
  },
  data(){
    return {
      cardChoosen:[],
      cardWons:[]
    }
  },
  methods:{    
    handleFlipCard(card){
      this.cardChoosen.push(card)
      if(this.cardChoosen.length > 2){
        this.cardChoosen.map(c => c.setCover())
        this.cardChoosen = []
      }else if(this.cardChoosen.length === 2){
        if(this.cardChoosen[0].image.name === this.cardChoosen[1].image.name){
          this.cardWons.push(card)
          this.cardChoosen.map(c => c.setRaised())
          this.cardChoosen = []
          this.$emit('match')
        }
      }
    },

  }
}
</script>

<style scoped>
#board{
  display: flex;
  flex-wrap: wrap;
  width: 400px;
  height: 300px;
  align-self: center;
}
</style>
