<template>
<div class="container">
    <span class="results">Your Reaction time is {{score}} ms</span>
    <p >{{rank}}</p>
</div>
  
</template>

<script>
    export default {
        props: ['score'],
        data(){
            return {
             rank: null

            }

        },
        mounted(){
            if(this.mounted < 250){
                this.rank = "Phew..... you've got a  ninja finger"
            }
            else if(this.score < 450){
                this.rank = "Rapid Reflexes"
            }
            else{
                this.rank = 'Snail pace'
            }
        }

}
</script>

<style scoped>
.results {
    background-color: grey;
    display: inline-blockx;
    width: 800px;
    padding: 10 30px;
}
.container {
    display: flex;
    flex-direction: column;
}

</style>