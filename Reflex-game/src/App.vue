<template>
  <div>
    <h1>Reflex Timer Game</h1>
    <button @click="start" :disabled='isPlaying' class="play">Play</button>
      <Block v-if="isPlaying" :delay="delay" @end='endGame'/>
      <Result v-if="showResult" :score="score"/>
  </div>
</template>

<script >
import Block from './components/Block.vue'
import Result from './components/Result.vue'
  export default{
    components:{
      Block,
      Result,
    },
    props: [],
    data(){
     return {
       isPlaying: false,
       delay: null,
       score: null,
       showResult: false
    }
    },
    methods:{
      start (){
        this.isPlaying = true,
        this.delay = 2000 + Math.random() + 4000
        this.showResult=false
      },
      endGame(reactionTime){
        this.score = reactionTime,
        this.isPlaying = false
        this.showResult= true
      }
    }
  }
</script>




<style scoped>
 h1 {
  font-size: 50px;
  text-align: center;
}
.play{
  padding: 5px 20px;
  border: 2px gray solid;
}
.disabled{
  border: 1px black;
}
@media (min-width: 1024px) {
  
}
</style>
