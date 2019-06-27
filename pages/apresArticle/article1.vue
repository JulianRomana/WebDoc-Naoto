<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" :src="img">
      <img class="secondImg" :src="img">
      <img class="thirdImg" :src="img">
      <img class="fourthImg" :src="img">
      <img class="fifthImg" :src="img">
      <img class="sixthImg" :src="img">
      <article class="txt">
        <p>{{ txt }}</p>
      </article>
      <article class="txt2">
        <p>{{ txt }}</p>
      </article>
      <article class="txt3">
        <p>{{ txt }}</p>
      </article>
      <nuxt-link to="videoArticle1">
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
    top: 250px;
    right: 350px;
  }
  .secondImg {
    display: none;
    position: fixed;
    top: 100px;
    left: 150px;
    z-index: 3;
  }
  .thirdImg {
    display: none;
    position: fixed;
    top: 270px;
    left: 500px;
    z-index: 2;
  }
  .fourthImg {
    display: none;
    position: fixed;
    top: 130px;
    left: 1000px;
    z-index: 1;
  }
  .fifthImg {
    display: none;
    position: fixed;
    top: 130px;
    left: 1000px;
    z-index: 1;
  }
  .sixthImg {
    display: none;
    position: fixed;
    top: 130px;
    left: 1000px;
    z-index: 1;
  }
  .txt {
    z-index: 1;
    background-color: white;
    width: 585px;
    height: 321px;
    position: fixed;
    top: 180px;
    right: 700px;
  }
  .txt2 {
    display: none;
    z-index: 3;
    background-color: white;
    width: 585px;
    height: 321px;
    position: fixed;
    top: 220px;
    right: 430px;
  }
  .txt3 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 400px;
    height: 381px;
    position: fixed;
    top: 270px;
    right: 120px;
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
    let img5 = document.querySelector(".fifthImg");
    let img6 = document.querySelector(".sixthImg");
    let txt2 = document.querySelector(".txt2");
    let txt3 = document.querySelector(".txt3");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      console.log(scroll);
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      if (scroll > 502) {
        scroll = scroll - 502;
        img2.style.display = "block";
        txt2.style.display = "block";
        txt3.style.display = "block";
        button.style.display = "flex";
        img2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt2.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        txt3.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        img2.style.display = "none";
        txt2.style.display = "none";
        txt3.style.display = "none";
        button.style.display = "none";
      }
    });
  }
};
</script>