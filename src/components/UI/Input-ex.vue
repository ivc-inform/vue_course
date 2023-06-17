<template>
  <input :value="value" @input="updateInput" type="text" class="input"/>
</template>

<script>
export default {
  name: "input-ex",
  props: {
    value: [String, Number]
  },
  methods: {
    updateInput(event){
      this.$emit("update:value", event.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 15px;
  margin-top: 15px;
}
</style>