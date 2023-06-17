<template>
  <div class="app">
    <post-form
        @create="createPost"
    />
    <post-list
        :posts="posts"
    />
  </div>
</template>

<script lang="js">
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";

export default {
  components: {PostList, PostForm},
  data() {
    return {
      posts: [
        {id: 1, title: "JavaScript", body: "Описание поста"},
        {id: 2, title: "TypeScript", body: "Описание поста"},
        {id: 3, title: "Java", body: "Описание поста"},
      ],
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
    }
  },
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}


.app {
  padding: 20px;
}


</style>