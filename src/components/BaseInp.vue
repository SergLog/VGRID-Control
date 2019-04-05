<template>
  <div>
    <b-input v-model="val" v-on:input="onValueChange"></b-input>
  </div>
 </template>

<script>
  export default {
  name: 'BaseInput',
  props: {
    value: null
  },  
  data() {
      return { val: this.value}
  },
  methods: {
    onValueChange: function() {
      this.$emit('update:value', this.val);
    }
  }
  }
</script>


<style scoped>
</style>
