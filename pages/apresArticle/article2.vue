<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" :src="img">
      <article class="txt">
        <p>{{ txt }}</p>
      </article>
      <nuxt-link to="fukushimaVideo">
        <span class="returnButton">suivant</span>
      </nuxt-link>
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
  position: fixed;
  z-index: 0;
}
.apresScreen {
  background-image: url("../../static/images/apres.jpg");
  background-size: cover;
  background-position: center;
  height: 180vh;
  width: 100vw;
  font-family: league spartan;
  .returnButton {
    position: fixed;
    top: 300px;
    right: 0;
    width: 70px;
    height: 70px;
    color: black;
    background-color: white;
    border-radius: 50%;
    display: none;
    align-items: center;
    text-align: center;
    transition: 0.3s ease-in-out;
    cursor: pointer;
    &::after {
      content: "▶";
      display: block;
    }
    p {
      font-weight: bold;
    }
    &:hover {
      background-color: rgba(255, 255, 255, 0.561);
    }
  }
  h1 {
    font-size: 25px;
    position: fixed;
    top: 50px;
    left: 50px;
  }
  img {
    width: 403px;
    height: 402px;
    position: fixed;
    top: 150px;
    right: 750px;
  }
  .txt {
    z-index: 1;
    background-color: white;
    width: 585px;
    height: 321px;
    position: fixed;
    top: 100px;
    right: 240px;
  }
}
</style>
<script>
const axios = require("axios");
import Menu from "~/components/Menu.vue";
export default {
  head: {
    script: [
      {
        src: "https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.min.js"
      }
    ]
  },
  components: {
    Menu
  },
  data() {
    return {
      img1: null,
      img2: null,
      img3: null,
      img4: null,
      img5: null,
      img6: null,
      txt: null
    };
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.img = response.data[0].img;
      this.txt = response.data[0].content;
    });
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let button = document.querySelector(".returnButton");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      console.log(scroll);
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
    });
  }
};
</script>