<template>
  <div href="#" class="card" @click="flipCard()">
    <img :src="require(`@/assets/${picture}`)" :alt="'card_'+index" />
  </div>
</template>

<script>
const cover = 'images/blank.png'
const raised = 'images/white.png'
export default {
  name: 'Card',
  props: {
    index:{
      type:Number,
      required:true
    },
    image:{
      type:Object
    }
  },
  data(){
    return {
      id:0,      
      picture: cover
    }
  },
  methods:{
    flipCard(){
      if(this.picture === cover){
        this.picture = this.image.img
        this.$emit("flip-card", this)
      }
    },
    setCover(){
      this.picture = cover
    },
    setRaised(){
      this.picture = raised
    }
  }
}
</script>

<style scoped>
.card{
  display: flex;
  margin:0;
  padding:0;
}
</style>
