<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>

.btn {
  padding: 10px 15px;
  background: none;
  border: 1px solid teal;
  color: teal;
}
</style>