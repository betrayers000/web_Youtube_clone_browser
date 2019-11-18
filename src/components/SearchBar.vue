<template>
  <div class="text-center">
    <input class="w-75" type="text" @keydown.enter="onInput">
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods:{
    onInput(e){
      // console.log(e.target.value)
      this.$emit('inputChange', e.target.value)
    }
  }
}
</script>

<style>

</style>