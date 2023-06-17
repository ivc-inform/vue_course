<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <button-ex @click="showDialog">Создать пост</button-ex>
    <dialog-ex v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </dialog-ex>

    <post-list
        :posts="posts"
        @remove="removePost"
    />
  </div>
</template>

<script lang="js">
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import DialogEx from "@/components/UI/DialogEx.vue";

export default {
  components: {DialogEx, PostList, PostForm},
  data() {
    return {
      posts: [
        {id: 1, title: "JavaScript", body: "Описание поста"},
        {id: 2, title: "TypeScript", body: "Описание поста"},
        {id: 3, title: "Java", body: "Описание поста"},
      ],
      dialogVisible: false
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
    },
    removePost(post) {
      this.posts = this.posts.filter(_ => _.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
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