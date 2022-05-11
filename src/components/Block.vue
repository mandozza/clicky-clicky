<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
   Click ME!!!
  </div>
</template>

<script>
export default {
  props: ['delayTimer'],
  data() {
    return {
      showBlock: false,
      timer: null,
      timeToClick: 0
    }
  },
  mounted() {
    console.log('mounted', )
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delayTimer)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.timeToClick += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      this.$emit('endOfGame', this.timeToClick)
    }
  }
}
</script>

<style>
  .block {
    background-color: #999;
    border-radius: 12px;
    color: #fff;
    font-size: 1.5rem;
    font-weight: bold;
    margin: 50px auto;
    padding: 80px 60px;
    text-align: center;
    width: 40%;
  }
</style>
