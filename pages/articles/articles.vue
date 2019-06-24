<template>
  <div class="articles">
    <ul class="articles__list">
      <li class="article" v-for="article in this.array">
        <h2 class="article__name">{{article.name}}</h2>
        <img class="article__img" :src="article.img" alt>
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
.articles__list {
  display: flex;
  width: 100vw;
  height: 100vh;
  flex-direction: column;
}
.article {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  .article__name {
    font-size: 36px;
  }
  .article__img {
    height: 200px;
  }
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
  }
};
</script>