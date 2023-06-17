<template>
  <form @submit.prevent>
    <h4>Создание поста</h4>
    <input @input="title=$event.target.value" v-bind:value="title" class="input" type="text" placeholder="Названиие">
    <input @input="body=$event.target.value" v-bind:value="body" class="input" type="text" placeholder="Описание">
    <button class="btn" @click="createPost">Создать</button>
  </form>
</template>

<script>
export default {}
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