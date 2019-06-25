<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img :src="img">
      <article>
        <p>{{ txt }}</p>
      </article>
    </section>
    <Menu></Menu>
  </div>
</template>
<style lang="scss" scoped>
.apresScreen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(255, 255, 255, 0.541);
  position: absolute;
  z-index: 0;
}
.apresScreen {
  background-image: url("../../static/images/apres.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  width: 100vw;
  font-family: league spartan;

  h1 {
    font-size: 25px;
    position: absolute;
    top: 50px;
    left: 50px;
  }
  img {
    width: 403px;
    height: 402px;
    position: absolute;
    top: 200px;
    right: 700px;
  }
  article {
    background-color: white;
    width: 585px;
    height: 321px;
    position: absolute;
    top: 100px;
    right: 200px;
  }
}
</style>
<script>
const axios = require("axios");
import Menu from "~/components/Menu.vue";
export default {
  components: {
    Menu
  },
  data() {
    return {
      img: null,
      txt: null
    };
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.img = response.data[0].img;
      this.txt = response.data[0].content;
    });
  }
};
</script>