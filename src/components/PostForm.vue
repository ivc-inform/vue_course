<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input
        v-bind:value="post.title"
        @input="post.title=$event.target.value"
        class="input"
        type="text"
        placeholder="Названиие">
    <input
        v-bind:value="post.body"
        @input="post.body=$event.target.value"
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

.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  border: 1px solid teal;
}

form {
  display: flex;
  flex-direction: column;
}
</style>