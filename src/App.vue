<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <div class="app_btns">
      <button-ex @click="showDialog">Создать пост</button-ex>
      <select-ex v-model="selectedSort"/>
    </div>

    <dialog-ex v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </dialog-ex>

    <post-list
        :posts="posts"
        @remove="removePost"
        v-if="!isLoading"
    />
    <div v-else>
      Идет загрузка...
    </div>
  </div>

</template>

<script lang="js">
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import DialogEx from "@/components/UI/DialogEx.vue";
import axios from "axios";
import SelectEx from "@/components/UI/SelectEx.vue";

export default {
  components: {SelectEx, DialogEx, PostList, PostForm},
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isLoading: false,
      selectedSort: ""
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(_ => _.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true
    },
    async fetchPosts() {
      try {
        this.isLoading = true
        const response = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10")
        this.posts = response.data
      } catch (e) {
        alert("Ошибка")
      } finally {
        this.isLoading = false
      }
    },
  },
  mounted() {
    this.fetchPosts()
  }
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

.app_btns {
  display: flex;
  justify-content: space-between;
  margin: 15px 0;
}


</style>