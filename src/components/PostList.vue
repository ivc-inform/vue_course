<template>
  <div>
    <h3>Список пользователей</h3>
    <post-item
        v-for="post in posts"
        :post="post"/>
  </div>
</template>

<script lang="js">
import PostItem from "@/components/PostItem.vue";

export default {
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      require: this
    }
  }
}
</script>

<style scoped>

</style>