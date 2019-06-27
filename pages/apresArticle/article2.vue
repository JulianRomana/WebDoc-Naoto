<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" :src="img1">
      <img class="secondImg" :src="img2">
      <img class="thirdImg" :src="img3">
      <img class="fourthImg" :src="img4">
      <article class="txt">
        <p>{{ txt }}</p>
      </article>
      <article class="txt2">
        <p>{{ txt2 }}</p>
      </article>
      <article class="txt3">
        <p>{{ txt3 }}</p>
      </article>
      <article class="txt4">
        <p>{{ txt4 }}</p>
      </article>
      <article class="txt5">
        <p>{{ txt5 }}</p>
      </article>
      <nuxt-link class="return" to="videoArticle2">
        <Retour Retour="Vidéo" class="returnButton"></Retour>
      </nuxt-link>
    </section>
    <Menu></Menu>
  </div>
</template>
<style lang="scss" scoped>
.returnButton {
  position: fixed;
  top: 40%;
  left: 10px;
}
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
  h1 {
    font-size: 25px;
    position: fixed;
    top: 50px;
    left: 50px;
  }
  article {
    background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: fixed;
    bottom: 50px;
    right: 200px;
    width: 580px;
    height: 360px;
    font-size: 18px;
    font-family: oswald;
    z-index: 1;
    padding: 0px 40px 0px 40px;
    &::first-line {
      font-weight: bold;
      font-size: 19px;
    }
    p {
      margin: 20px 20px 0px 20px;
      line-height: 1.7rem;
    }
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
    left: 250px;
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
    top: 240px;
    left: 580px;
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
    width: 480px;
    height: 200px;
    position: fixed;
    top: 420px;
    right: 880px;
  }
  .txt3 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 420px;
    height: 200px;
    position: fixed;
    top: 460px;
    right: 370px;
  }
  .txt4 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 460px;
    height: 321px;
    position: fixed;
    top: 100px;
    left: 100px;
  }
  .txt5 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 420px;
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
import Retour from "~/components/Retour";
import $ from "jquery";
export default {
  components: {
    Menu,
    Retour
  },
  data() {
    return {
      img1: null,
      img2: null,
      img3: null,
      img4: null,
      txt: null,
      txt2: null,
      txt3: null,
      txt4: null,
      txt5: null
    };
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.img1 = response.data[0].img1;
      this.img2 = response.data[0].img4;
      this.img3 = response.data[0].img5;
      this.img4 = response.data[0].img3;
      this.txt = response.data[0].content;
      this.txt2 = response.data[0].content2;
      this.txt3 = response.data[0].content3;
      this.txt4 = response.data[0].content7;
      this.txt5 = response.data[0].content8;
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