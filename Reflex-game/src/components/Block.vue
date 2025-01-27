<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
    click me
  </div>
</template>

<script>
import { onMounted } from 'vue'
export default {
    props: {
    delay: {
      type: Number,
      required: true,
    }},
    data(){
      return{
        showBlock: false,
        reactionTime : 0,
        timer : null
      }
    },
    mounted (){
      console.log("component mounted")
     setTimeout(() => {
      this.showBlock = true
      this.startTimer()
      console.log(this.delay)
      
     }, this.delay);

    },
    methods:{

      startTimer(){
        this.timer = setInterval(()=> {
          this.reactionTime += 10
        }, 10)
      },
      stopTimer (){
        clearInterval(this.timer),
        this.$emit('end', this.reactionTime)
      }

    }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: gray;
    color: white;
    text-align: center;
    padding: 100px 0;
}

</style>