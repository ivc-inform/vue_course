<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <input-ex
        v-model="searchQuery"
        aria-placeholder="Поиск..."
        style="width: 100%"
    />
    <div class="app_btns">
      <button-ex @click="showDialog">Создать пост</button-ex>
      <select-ex v-model="selectedSort" :options="sortOptions"/>
    </div>

    <dialog-ex v-model:show="dialogVisible">
      <post-form
          @create="createPost"
      />
    </dialog-ex>

    <post-list
        :posts="sortedAndSearchPost"
        @remove="removePost"
        v-if="!isLoading"
    />
    <div v-else>
      Идет загрузка...
    </div>
    <div class="page__wrapper">
      <div
          v-for="pageNumber in totalPage"
          :key="pageNumber"
          class="page"
          :class="{
            'current-page': page === pageNumber
          }"
      > {{ pageNumber }}
      </div>
    </div>
  </div>

</template>

<script lang="js">
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import DialogEx from "@/components/UI/DialogEx.vue";
import axios from "axios";
import SelectEx from "@/components/UI/SelectEx.vue";
import InputEx from "@/components/UI/Input-ex.vue";

export default {
  components: {InputEx, SelectEx, DialogEx, PostList, PostForm},
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isLoading: false,
      selectedSort: "",
      searchQuery: "",
      page: 1,
      limit: 10,
      totalPage: 0,
      sortOptions: [
        {
          value: "title",
          name: "По названию"
        },
        {
          value: "body",
          name: "По описанию"
        }
      ]
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
        const response = await axios.get("https://jsonplaceholder.typicode.com/posts", {
          params: {
            _page: this.page,
            _limit: this.limit,
          }
        })
        this.totalPage = Math.ceil(response.headers['x-total-count'] / this.limit)
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
  },
  computed: {
    sortedPost() {
      return [...this.posts].sort((a, b) => a[this.selectedSort]?.localeCompare(b[this.selectedSort]))
    },
    sortedAndSearchPost() {
      return this.sortedPost.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }
  },
  watch: {}
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

.page__wrapper {
  display: flex;
  margin-top: 15px;
}

.page {
  border: 1px solid black;
  padding: 10px;
}

.current-page {
  border: 3px solid teal;
  border-radius: 10px;
}
</style>