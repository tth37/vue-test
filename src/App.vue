<template>
  <h1>tth37 timer game!!!</h1>
  <div v-if="showResult">
    <Result :score="passedTime">
    </Result>
  </div>
  <button v-show="!isPlaying" @click="playNewGame">play!</button>
  <div v-if="endOfCountDown">
    <Block @clickBlock="clickBlock" />
  </div>
</template>

<script>

import Block from './components/Block'
import Result from './components/Result'

function randomNum(minNum, maxNum) {
  return parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10)
}

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      endOfCountDown: false,
      counter: 0,
      showResult: false,
      passedTime: 0,
    }
  },
  methods: {
    playNewGame() {
      this.showResult = false
      this.isPlaying = true
      this.endOfCountDown = false
      let pauseTime = randomNum(2000, 7000)
      setTimeout(() => {
        this.endOfCountDown = true
        this.counter = Date.now()
      }, pauseTime)
    },
    clickBlock() {
      this.endOfCountDown = false
      this.passedTime = Date.now() - this.counter
      this.showResult = true
      this.isPlaying = false
    }
  },

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
