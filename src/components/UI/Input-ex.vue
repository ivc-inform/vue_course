<template>
  <input :value="modelValue" @input="updateInput" type="text" class="input"/>
</template>

<script>
export default {
  name: "input-ex",
  props: {
    modelValue: [String, Number]
  },
  methods: {
    updateInput(event){
      this.$emit("update:modelValue", event.target.value)
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