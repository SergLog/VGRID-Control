<template>
<div>
  <b-form-input size="sm" type="text" v-bind:value="val"></b-form-input>
  </div>
 </template>


<script>
  export default {
  name: 'BaseInput',
  props: {
    val: String
  },  
  data() {
      return {
}
  }
  }
</script>


<style scoped>
</style>
