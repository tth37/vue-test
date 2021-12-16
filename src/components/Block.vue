<template>
  <div class="block" :class="blockClass" @click="clickBlock">
    <span class="content">{{ blockContent }}</span>
  </div>
</template>

<script>
export default {
  props: [ 'delay' ],
  data() {
    return {
      blockClass: 'forbidden',
      blockContent: 'Get ready...',
      isReady: false,
      timeOut: null,
      startTime: 0,
      endTime: 0,
      reactionTime: 0
    }
  },
  mounted() {
    console.log(this.delay)
    this.timeOut = setTimeout(() => {
      this.blockClass = 'available'
      this.blockContent = 'Click me!'
      this.isReady = true
      this.timerStart()
    }, this.delay)
  },
  methods: {
    clickBlock() {
      if (this.isReady === false) {
        clearTimeout(this.timeOut)
        this.$emit('clickBlock', -1)
        return
      }
      this.timerStop()
      clearTimeout(this.timeOut)
      // console.log(this.reactionTime)
      this.$emit('clickBlock', this.reactionTime)
      return
    },
    timerStart() {
      this.startTime = Date.now()
    },
    timerStop() {
      this.endTime = Date.now()
      this.reactionTime = this.endTime - this.startTime
    }
  }
}
</script>

<style>
.block {
  margin: 30px auto;
  border-radius: 20px;
  height: 200px;
  width: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.forbidden {
  background-color: salmon;
}

.available {
  background-color: springgreen;
}


</style>