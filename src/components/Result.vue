<template>
  <div class="result">
    <p>Your Score: {{ score }}ms</p>
    <p>{{ getComment }}</p>
  </div>
</template>


<script>
export default {
  name: 'Result',
  props: [ 'score' ],
  data() {
    return {
      comment: '',
    }
  },
  methods: {

  },
  computed: {
    getComment() {
      if (this.score === 99999)
        return 'Fuck!!! You cheat!!!! Fuckkk!'
      if (this.score >= 500) {
        return 'You! Vegetable! Fuck!'
      } else if (this.score >= 300) {
        return 'Just soso la!'
      } else if (this.score >= 100) {
        return 'have some south west!'
      }
      return 'fuck! true god!!'
    }
  }
}

</script>

<style>

.result {
  color: red;
}

</style>