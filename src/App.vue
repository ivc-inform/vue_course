<template>
  <div class="app">
    <form @submit.prevent>
      <h4>Создание поста</h4>
      <input @input="title=$event.target.value" v-bind:value="title" class="input" type="text" placeholder="Названиие">
      <input @input="body=$event.target.value" v-bind:value="body" class="input" type="text" placeholder="Описание">
      <button class="btn" @click="createPost">Создать</button>
    </form>
    <div class="post" v-for="post in posts">
      <div><strong>Название: </strong>{{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
  </div>
</template>

<script lang="js">
export default {
  data() {
    return {
      posts: [
        {id: 1, title: "JavaScript", body: "Описание поста"},
        {id: 2, title: "TypeScript", body: "Описание поста"},
        {id: 3, title: "Java", body: "Описание поста"},
      ],
      title: "",
      body: ""
    }
  },
  methods: {
    createPost() {
      const newPost = {
        id: Date.now(),
        title: this.title,
        body: this.body,
      }

      this.posts.push(newPost)
      this.title = ""
      this.body = ""
    },
  },
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.post {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}

.input {
  width: 100%;
  border: 1px solid teal;
  padding: 15px;
  margin-top: 15px;
}

.app {
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
}

.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  border: 1px solid teal;
}
</style>