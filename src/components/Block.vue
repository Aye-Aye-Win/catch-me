<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click here</div>
</template>

<script>

export default {
props: ['delay'],
data(){
    return {
    showBlock: false,
    score:0,
    timer: null
    } 
  },
  mounted(){
    setTimeout(()=>{
        this.showBlock= true,
        this.startTimer();
    },this.delay);
  },
  methods:{
    startTimer(){
      this.timer = setInterval(()=>{
        this.score += 50;
      },70)
    },
    stopTimer(){
      clearInterval(this.timer);
      this.$emit("endGame",this.score)
    }
  } 
}

</script>

<style>
.block{
    width: 500px;
    height: 400px;
    margin: 20px auto;
    padding-top: 30px;
    border-radius: 20px;
    border: 4px solid black;
}
</style>
