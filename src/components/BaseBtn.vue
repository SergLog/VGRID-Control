<template>
  <b-button class="BaseBtn" size="sm" variant="primary">
    <slot></slot>
  </b-button>
</template>

<script>
  export default {
  name: 'BaseBtn'}
</script>

<style scoped>
  .BaseBtn {
    margin: 10px;
}
</style>