<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" :src="img">
      <img class="secondImg" :src="img">
      <img class="thirdImg" :src="img">
      <img class="fourthImg" :src="img">
      <article class="txt">
        <p>{{ txt }}</p>
      </article>
      <article class="txt2">
        <p>{{ txt }}</p>
      </article>
      <article class="txt3">
        <p>{{ txt }}</p>
      </article>
      <article class="txt4">
        <p>{{ txt }}</p>
      </article>
      <article class="txt5">
        <p>{{ txt }}</p>
      </article>
      <nuxt-link to="videoArticle2">
        <span class="returnButton">Vidéo</span>
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
  height: 245vh;
  width: 100vw;
  font-family: league spartan;
  .returnButton {
    position: fixed;
    top: 300px;
    left: 0;
    width: 70px;
    height: 70px;
    color: black;
    background-color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    text-align: center;
    transition: 0.3s ease-in-out;
    cursor: pointer;
    &::before {
      content: "◀";
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
  .secondImg {
    display: none;
    position: fixed;
    top: 30px;
    left: 350px;
    z-index: 3;
  }
  .thirdImg {
    display: none;
    position: fixed;
    top: 100px;
    left: 1000px;
    z-index: 2;
  }
  .fourthImg {
    display: none;
    position: fixed;
    top: 277px;
    left: 610px;
    z-index: 2;
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
  .txt2 {
    display: none;
    z-index: 3;
    background-color: white;
    width: 385px;
    height: 321px;
    position: fixed;
    top: 220px;
    right: 960px;
  }
  .txt3 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 385px;
    height: 321px;
    position: fixed;
    top: 340px;
    right: 300px;
  }
  .txt4 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 600px;
    height: 321px;
    position: fixed;
    top: 100px;
    left: 100px;
  }
  .txt5 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 385px;
    height: 321px;
    position: fixed;
    top: 100px;
    right: 40px;
  }
}
</style>
<script>
const axios = require("axios");
import Menu from "~/components/Menu.vue";
import $ from "jquery";
export default {
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
    let img2 = document.querySelector(".secondImg");
    let img3 = document.querySelector(".thirdImg");
    let img4 = document.querySelector(".fourthImg");
    let txt2 = document.querySelector(".txt2");
    let txt3 = document.querySelector(".txt3");
    let txt4 = document.querySelector(".txt4");
    let txt5 = document.querySelector(".txt5");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      console.log(scroll);
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      if (scroll > 502) {
        scroll = scroll - 502;
        img2.style.display = "block";
        img3.style.display = "block";
        txt2.style.display = "block";
        txt3.style.display = "block";
        img2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        img3.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt3.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        img2.style.display = "none";
        img3.style.display = "none";
        txt2.style.display = "none";
        txt3.style.display = "none";
      }
      if (scroll > 502) {
        scroll = scroll - 502;
        console.log(img4);
        img4.style.display = "block";
        txt4.style.display = "block";
        txt5.style.display = "block";
        img4.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt4.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt5.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        img4.style.display = "none";
        txt4.style.display = "none";
        txt5.style.display = "none";
      }
    });
  }
};
</script>