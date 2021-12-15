<template>
  <div class="block" @click="clickBlock" :class="{cheat: theme === 'cheatBlock' }">
    <div>FUCK ME!!</div>
  </div>
</template>


<script>

export default {
  name: 'Block',
  props: [ 'theme' ],
  data() {
    return {

    }
  },
  methods: {
    clickBlock() {
      this.$emit('clickBlock')
    }
  }
}

</script>

<style>
.block {
  display: block;
  background-color: aquamarine;
  margin: 50px auto;
  width: 200px;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;

}

.cheat {
  background-color: red;
}
</style>