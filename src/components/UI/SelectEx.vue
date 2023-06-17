<template>
  <select v-bind="modelValue" @change="changeOption">
    <option
        disabled value="">
      Выберите из списка
    </option>
    <option
        value=""
        v-for="option in options"
        :key="option.value"
        :value="option.value">
      {{ option.name}}
    </option>
  </select>
</template>

<script>
export default {
  name: "select-ex",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods:{
    changeOption(option){
      this.$emit("update:modelValue", option)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>