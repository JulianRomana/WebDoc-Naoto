<template>
  <div>
    <ul class="articles__list grid-container">
      <li class="article" v-for="article in this.array">
        <h2 class="article__name">{{article.name}}</h2>
        <img class="article__img" :src="article.img" alt>
        <button @click="checking" class="button"></button>
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
.grid-container {
  display: grid;
  grid-template-columns: 1fr;
  grid-template-rows: 1fr 1fr 1fr;
}
.button {
  display: inline-block;
  text-align: center;
  vertical-align: middle;
  padding: 12px 24px;
  border: 1px solid #a12727;
  border-radius: 8px;
  background: #ff4a4a;
  background: linear-gradient(to bottom, #ff4a4a, #992727);
  text-shadow: #591717 1px 1px 1px;
  font: normal normal bold 22px arial;
  color: #ffffff;
  text-decoration: none;
}
.button:hover,
.button:focus {
  background: #ff5959;
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    from(#ff5959),
    to(#b62f2f)
  );
  background: linear-gradient(to bottom, #ff5959, #b62f2f);
  color: #ffffff;
  text-decoration: none;
}
.button:active {
  background: #982727;
  background: -webkit-gradient(
    linear,
    left top,
    left bottom,
    from(#982727),
    to(#982727)
  );
  background: linear-gradient(to bottom, #982727, #982727);
}
.button:before {
  content: "\0000a0";
  display: inline-block;
  height: 24px;
  width: 24px;
  line-height: 24px;
  margin: 0 4px -6px -4px;
  position: relative;
  top: 0px;
  left: 4px;
  background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAYAAADgdz34AAAACXBIWXMAAA7EAAAOxAGVKw4bAAACMklEQVRIibWVsW4TQRCGv1mdAqI4ge0gkYgXoEhFneo6aEOLdBJ5gSiVa6BAPAAUh5BoAj0NV6Sho0hJQREJZKzEueIqjKwdit3De+u7ICRnZJ/3Zv+Z2f/f2bUAhiu0JrntmbfrGMcMzDrH4gc2mmgxGmT5Q+ANkHpXDTyuyuIj/zAT/JqedwMcAGNVu61qt4ExcNiBW/nGDMwwy3cVXgignqLCPeCHQK0OlwJbwFfxgR57eFEWx6ESScTIKnwD3iq8BJ4o/CJIEpvCDeAVcOBjW9YwaNkgy1PgHLhblcVZR94Qexv4DmxWZVHH8w2D1iYni9/1ItkAuAlMh1n+CPiCkwVgAty/KIv3HsM1SeoolwFs1yGzZ8fvLDADRt43RmQHZA+RPRXZwW00HjP7+el151lqGHQVagqYZqfVPRDEieviRh5rOnKZTon8+wwYuLH4j8vadJfHNQUsUUfSJxGAiCwlUt8/imewdAUF4oVaWEoUU0NVK2ATMIg4ecRpJQgiAu4gDbUtUctCpw1WEG6ybZKiiqhfvaNgtS3RSp5eiUDO+SuR9yDuKa1DN8KdmSB2Oe6VCDToon6JPKZajXcWFmjtPl6iOw/2mc8XR8Ap6GdHSE+Bo1vZPrC4tIviuygsNAPS+XyRVGXxzPtOAtzJIMs3cBff/3cR7jpIgd1hlk/CiUD/LYeRSUc8cYEWNWt0aqw8BT4oXO8Kxt20z9XqlB6Jula+VrtMorXZlf7p/wHAL9L6d7AWWwAAAABJRU5ErkJggg==")
    no-repeat left center transparent;
  background-size: 100% 100%;
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
      console.log(this.array);
    });
  }
};
</script>