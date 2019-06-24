<template>
  <div class="grid-container">
    <ul class="articles__list">
      <li v-model="article.active" class="article" v-for="article in this.array">
        <h2 class="article__name">{{article.name}}</h2>
        <p class="article__content">{{article.content}}</p>
        <img class="article__img" :src="article.img" :alt="article.name + ' image'">
        <button @click="checking(article.id)" ref="id" :data-id="article.id" class="deleteButton"></button>
      </li>
    </ul>
  </div>
</template>
<style scoped lang="scss">
.article {
  display: grid;
  grid-template-columns: 15% 39% 28% 15%;
}
</style>
<script>
const axios = require("axios");
export default {
  layout: "articlePage",
  data() {
    return {
      array: null
    };
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.array = response.data;
    });
  },
  methods: {
    checking(id) {
      axios({
        method: "delete",
        url: "http://localhost:7892/api/articles",
        data: {
          id: id
        }
      });
      this.$router.push("/articles/articles");
    }
  }
};
</script>