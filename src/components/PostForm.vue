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
    <button-ex
        class="btn"
        style="align-self: flex-end; margin-top: 15px"
        @click="createPost">Создать</button-ex>
  </form>
</template>

<script lang="js">
import ButtonEx from "@/components/ButtonEx.vue";

export default {
  components: {ButtonEx},
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