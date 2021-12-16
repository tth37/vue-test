<template>
  <h1>Reaction Time Game v2</h1>
  <Result :type="resultType" :score="resultScore" v-if="showResult" />
  <button class="btn-play" :disabled="isPlaying" @click="startGame">Play!</button>
  <Block v-if="isPlaying" :delay="delayTime" @clickBlock="clickBlock" />

</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delayTime: null,
      resultType: 'fail',
      resultScore: 0,
      showResult: false
    }
    
  },
  methods: {
    startGame() {
      this.delayTime = 2000 + Math.random() * 5000;
      this.isPlaying = true
      
      
    },
    clickBlock(score) {
      this.isPlaying = false
      if (score === -1) {
        this.resultType = 'fail'
        this.resultScore = 0
        this.showResult = true
        console.log('344')
        return
      }
      this.resultType = 'success'
      this.resultScore = score
      this.showResult = true
      console.log('2333')
    }
  }
}
</script>

<style scoped>
  h1 {
    text-align: center;
    margin-top: 50px;
  }
  .btn-play {
    display: block;
    margin: 30px auto;
    height: 35px;
    width: 75px;
    border-radius: 10px;
    border: 0;
    background-color: #abf54a;
    text-align: center;
    box-shadow: rgba(0, 0, 0, 0.1) 0px 4px;
  }
  .btn-play:hover {
    background-color: #86c03b;
  }
  .btn-play:active {
    background-color: #86c03b;
    transform: translateY(2px);
    box-shadow: rgba(0, 0, 0, 0.1) 0px 2px;
  }
  .btn-play:disabled {
    background-color: #dbfab3;
  }
</style>