<template>
  <div class="result">
    <h1>{{ resultContentType }}</h1>
    <p v-if="type==='success'">Your score: {{ score }} ms</p>
    <p v-if="type==='success'">{{ resultComment }}</p>
  </div>
</template>

<script>
export default {
  props: ['type', 'score'],
  data() {
    return {
      
    }
  },
  methods: {

  },
  computed: {
    resultContentType() {
      if (this.type === 'fail') {
        return 'You failed!'
      }
      return 'Congratulations!'
    },
    resultComment() {
      if (this.score <= 50) {
        return 'GOAT!'
      } else if (this.score <= 100) {
        return 'True God!'
      } else if (this.score <= 150) {
        return 'Well Done!'
      } else if (this.score <= 200) {
        return 'Good!'
      } else if (this.score <= 300) {
        return 'Just Soso!'
      } else if (this.score <= 500) {
        return "Too Bad!"
      } 
      return 'My grandma reacts faster than you : )'
    }
  }
}
</script>

<style>
.result {
  max-width: 350px;
  border-radius: 10px;
  border: rgb(255, 166, 0) 1px solid;
  margin: 40px auto;
  display: block;
}

.result h1 {
  font-size: 1.2em;
  text-align: center;
  color: blueviolet;

}

.result p {
  text-align: center;
}
</style>