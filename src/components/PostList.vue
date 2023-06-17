<template>
  <div v-if="posts.length > 0">
    <h3>Список пользователей</h3>
    <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else style="color: red">
    Список пуст.
  </h2>
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