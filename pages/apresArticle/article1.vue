<template>
  <div>
    <section id="apresScreen" class="apresScreen">
      <h1>L’APRÈS</h1>
      <img class="firstMove" :src="img1">
      <img class="secondImg" :src="img2">
      <article class="txt">
        <p>{{ txt }}</p>
      </article>
      <article class="txt2">
        <p>{{ txt2 }}</p>
      </article>
      <article class="txt3">
        <p>{{ txt3 }}</p>
      </article>
      <nuxt-link to="videoArticle2">
        <VoirArticle Article="Suite Vidéo" class="returnButton"></VoirArticle>
      </nuxt-link>
    </section>
    <Menu></Menu>
    <nuxt-link class="return" to="videoArticle1">
      <Retour Retour="Vidéo" class="returnVideo"></Retour>
    </nuxt-link>
  </div>
</template>
<style lang="scss" scoped>
.returnVideo {
  position: fixed;
  top: 40%;
  left: 10px;
  z-index: 5;
}
.return {
  color: black;
  background-color: white;
  &:hover {
    color: black;
    background-color: rgba(255, 255, 255, 0.253);
  }
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
    height: 240px;
    position: fixed;
    top: 180px;
    right: 700px;
  }
  .txt2 {
    display: none;
    z-index: 3;
    background-color: white;
    width: 500px;
    height: 310px;
    position: fixed;
    top: 220px;
    right: 520px;
  }
  .txt3 {
    display: none;
    z-index: 4;
    background-color: white;
    width: 400px;
    height: 260px;
    position: fixed;
    top: 340px;
    right: 110px;
  }
}
</style>
<script>
const axios = require("axios");
import Menu from "~/components/Menu.vue";
import VoirArticle from "~/components/VoirArticle";
import Retour from "~/components/Retour";
import $ from "jquery";
export default {
  components: {
    Menu,
    Retour,
    VoirArticle
  },
  data() {
    return {
      img1: null,
      img2: null,
      txt: null,
      txt2: null,
      txt3: null
    };
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      console.log(response.data[0]);
      this.img1 = response.data[0].img2;
      this.img2 = response.data[0].img6;
      this.txt = response.data[0].content4;
      this.txt2 = response.data[0].content5;
      this.txt3 = response.data[0].content6;
    });
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let button = document.querySelector(".returnButton");
    let img2 = document.querySelector(".secondImg");
    let txt2 = document.querySelector(".txt2");
    let txt3 = document.querySelector(".txt3");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
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