<template>
  <div class="block" @click="clickBlock">
    <div>FUCK ME!!</div>
  </div>
</template>


<script>

export default {
  name: 'Block',
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
</style>