<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>CATASTROPHE NUCLÉAIRE DE FUKUSHIMA</h1>
      <figure>
        <img class="firstMove" src="../../static/images/catastrophe/catastrophe-1.png" alt />
        <img class="secondImg" src="../../static/images/catastrophe/catastrophe-2.png" alt />
        <img class="thirdImg" src="../../static/images/catastrophe/catastrophe-3.png" alt />
        <img class="fourthImg" src="../../static/images/catastrophe/catastrophe-4.png" alt />
        <figcaption class="txt">
          <p>
            <span>Suite au tremblement de terre</span> qui a causé une panne d’électricité, et au tsunami qui a submergé la centrale puis mis hors service le système de refroidissement des réacteurs, les réacteurs 1,2 et 3 sont entrés en fusion, ce qui a causé plusieurs explosions a l’intérieur de la centrale sur plusieurs jours.
            <br />
            <br />Cet incident nucléaire est un accident de niveau 7 sur l’échelle de Richter, et équivaut à celui de Tchernobyl.
            <br />
            <br />Dès les premiers jours et encore aujourd’hui, d'importants rejets sont dispersés dans l'air. Ils se déplacent au gré des vent, et en raison de fuites continues, les rejets touches le littoral proche, les fonds marins et l’Océan Pacifique.
          </p>
        </figcaption>
      </figure>
      <aside>
        <h2>216 Md</h2>
        <p>D'Euros de dégats</p>
      </aside>
      <Menu></Menu>
      <nuxt-link class="return" to="fukushimaVideo">
        <Retour Retour="Vidéo" class="returnButton"></Retour>
      </nuxt-link>
      <nuxt-link class="start" to="../seisme/seisme">
        <VoirArticle Article="Suite" class="watchArticle"></VoirArticle>
      </nuxt-link>
    </section>
  </div>
</template>

<style scoped lang="scss">
.watchArticle {
  background-color: white;
  color: black;
  display: block;
  text-align: center;
  padding-top: 28px;
  &:hover {
    background-color: rgba(255, 255, 255, 0.507);
  }
}
.return {
  color: black;
}
.singleImage {
  display: none;
}
.fukushima__wrapper {
  width: 100vw;
  height: 180vh;
  background-color: white;
  background-image: url("../../static/images/catastrophe/blurryFukushima.png");
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
}
aside {
  position: fixed;
  right: 100px;
  top: 35%;
  text-align: center;
  &::after {
    position: absolute;
    top: -300px;
    content: "";
    width: 2px;
    background-color: black;
    animation: beforeSize 2s ease-in-out forwards;
  }
  h2 {
    opacity: 0;
    font-size: 36px;
    font-family: League Spartan;
    animation: textOpacity 0.5s ease-in-out 2s forwards;
  }
  p {
    opacity: 0;
    font-family: League Spartan;
    animation: textOpacity 0.5s ease-in-out 2s forwards;
  }
}
.content {
  height: 80%;
  width: 100%;
}
figure {
  position: relative;
  width: 955px;
  height: 100%;
  img:nth-child(1) {
    position: fixed;
    top: 100px;
    left: 150px;
    z-index: 1;
  }
  .secondImg {
    display: none;
    position: fixed;
    top: 130px;
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

  figcaption {
    background-color: rgb(255, 255, 255);
    box-shadow: -2px -2px 4px -10px #656565;
    border: none;
    position: fixed;
    bottom: 69px;
    right: 330px;
    width: 580px;
    height: 385px;
    font-size: 18px;
    z-index: 1;
    p {
      margin: 20px 40px 25px 40px;
      line-height: 1.7rem;
      span {
        font-weight: bold;
        font-family: oswald;
      }
    }
  }
}
h1 {
  text-align: left;
  margin-left: 150px;
  padding: 50px 0px 50px;
  font-size: 20px;
  position: fixed;
  top: 0;
  left: 30px;
}
.returnButton {
  position: fixed;
  top: 40%;
  left: 10px;
}
.start {
  display: none;
}
@keyframes beforeSize {
  0% {
    height: 0px;
  }
  100% {
    height: 270px;
  }
}
@keyframes textOpacity {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
<script>
import Menu from "~/components/Menu.vue";
import Retour from "~/components/Retour.vue";
import VoirArticle from "~/components/VoirArticle";
import $ from "jquery";
export default {
  components: {
    Menu,
    Retour,
    VoirArticle
  },
  mounted() {
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let aside = document.querySelector("aside");
    let second = document.querySelector(".secondImg");
    let third = document.querySelector(".thirdImg");
    let fourth = document.querySelector(".fourthImg");
    let next = document.querySelector(".start");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      if (scroll > 502) {
        scroll = scroll - 502;
        second.style.display = "block";
        third.style.display = "block";
        fourth.style.display = "block";
        next.style.display = "flex";
        aside.style.display = "none";
        second.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        third.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        fourth.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        second.style.display = "none";
        third.style.display = "none";
        aside.style.display = "block";
        next.style.display = "none";
        fourth.style.display = "none";
      }
    });
  }
};
</script>