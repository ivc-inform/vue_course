<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input-ex
        v-model:value="post.title"
        type="text"
        placeholder="Названиие"/>
    <input-ex
        v-model="post.body"
        type="text"
        placeholder="Описание"/>
    <button-ex
        class="btn"
        style="align-self: flex-end; margin-top: 15px"
        @click="createPost">Создать
    </button-ex>
  </form>
</template>

<script lang="js">

import InputEx from "@/components/UI/Input-ex.vue";

export default {
  components: {InputEx},
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


form {
  display: flex;
  flex-direction: column;
}
</style>