<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Названиие">
    <input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Описание">
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>

<script lang="js">
export default {
  data() {
    return {
      post: {
        title: "",
        body: ""
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: "",
        body: ""
      }
    }
  }
}
</script>

<style scoped>

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 15px;
  margin-top: 15px;
}


form {
  display: flex;
  flex-direction: column;
}
</style>