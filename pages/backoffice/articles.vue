<template>
  <div>
    <ul class="articles__list grid-container">
      <li class="article" v-for="article in this.array">
        <h2 class="article__name">{{article.name}}</h2>
        <p>{{article.content}}</p>
        <img class="article__img" :src="article.img" alt />
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
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
  }
};
</script>