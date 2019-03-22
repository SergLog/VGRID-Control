<template>
<b-select :options="options"></b-select>
<!-- <b-select v-model="selectedvalue" :options="options"></b-select> -->
 </template>


<script>
  export default {
  name: 'BaseSelect',
  props: {
    options: []
  },  
  data() {
      return {
}
  }
  }
</script>


<style scoped>
</style>
