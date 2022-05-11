<template>
  <div class="results" :class="scoreClass">
    <h1>{{ score }} ms - {{ responseText }}</h1>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
     scoreClass: null,
     responseText: null
    }
  },
  mounted(){
    if(this.score < 300){
      this.scoreClass = 'fast'
      this.responseText = 'You are fast!'
    } else if(this.score < 500){
      this.scoreClass = 'ok'
      this.responseText = 'Not bad but you can be faster!'
    } else {
      this.scoreClass = 'slow'
      this.responseText = 'Too slow! Next time bring you A game!'
    }
  }
}
</script>

<style>
  .results {
    border-radius: 20px;
    border: 1px solid #ccc;
    color:#000;
    margin: 60px auto;
    padding: 60px;
    width:60%;
  }
  .fast{
    background: green;
    color:yellow;
  }
  .ok{
    background: yellow;
  }
  .slow{
    background: red;
    color:white;
  }
</style>
