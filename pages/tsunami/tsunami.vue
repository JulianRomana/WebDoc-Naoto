<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>LE TSUNAMI</h1>
      <figure>
        <img class="firstMove" src="../../static/images/tsunami/tsunami-1.png" alt />
        <img class="secondImg" src="../../static/images/tsunami/tsunami-2.png" alt />
        <img class="thirdImg" src="../../static/images/tsunami/tsunami-3.png" alt />
        <img class="fourthImg" src="../../static/images/tsunami/tsunami-4.png" alt />
        <figcaption class="txt">
          <p>
            10 minutes après le tremblement de Terre, un tsunami eu lieu. Des vagues entre 10 et 15 mètres, atteignant même plus de 30 mètres de haut se sont abattues sur les côtes pacifiques du Japon.
            <br />
            <br />Celles ci se sont étendues jusqu’à 10km dans les villes de Iwate Fukushima et Miyagi, et ont détruit plus de 600km de côtes.
            <br />
            <br />Le tsunami est la cause de plus de 90% des dégâts matériels et des morts. Ce tsunami à aussi provoqué une submersion du système de refroidissement de la centrale de Fukushima .
          </p>
        </figcaption>
      </figure>
      <aside>
        <h2>10 804</h2>
        <p>Décès Confirmés</p>
      </aside>
      <Menu></Menu>
      <nuxt-link class="link" to="../seisme/seisme">
        <Retour class="returnButton" Retour="Retour"></Retour>
      </nuxt-link>
    </section>
  </div>
</template>

<style scoped lang="scss">
.link {
  color: black;
  &:hover {
    color: black;
  }
}
.singleImage {
  display: none;
}
.fukushima__wrapper {
  width: 100vw;
  height: 180vh;
  background-color: white;
  background-image: url("../../static/images/tsunami/tsunamiBackground.png");
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
}
aside {
  display: none;
  position: fixed;
  left: 100px;
  bottom: 30%;
  text-align: center;
  &::after {
    position: absolute;
    top: 70px;
    content: "";
    width: 2px;
    background-color: black;
    animation: beforeSize 2s ease-in-out forwards;
  }
  h2 {
    opacity: 0;
    font-size: 36px;
    font-family: League Spartan;
    animation: textOpacity 0.5s ease-in-out forwards;
  }
  p {
    opacity: 0;
    font-family: League Spartan;
    animation: textOpacity 0.5s ease-in-out forwards;
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
    left: 200px;
    z-index: 1;
  }
  .secondImg {
    display: none;
    position: fixed;
    top: 70px;
    left: 180px;
    z-index: 3;
  }
  .thirdImg {
    display: none;
    position: fixed;
    top: 240px;
    left: 530px;
    z-index: 2;
  }
  .fourthImg {
    display: none;
    position: fixed;
    top: 100px;
    left: 1030px;
    z-index: 1;
  }
  figcaption {
    background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: fixed;
    bottom: 50px;
    right: 200px;
    width: 580px;
    height: 360px;
    font-size: 18px;
    z-index: 1;
    &::first-line {
      font-weight: bold;
      font-size: 19px;
    }
    p {
      margin: 20px 20px 0px 20px;
      line-height: 1.7rem;
    }
  }
}
h1 {
  margin-left: 150px;
  font-size: 20px;
  position: fixed;
  top: 20px;
  left: 30px;
}
.returnButton {
  position: fixed;
  top: 40%;
  left: 10px;
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
import $ from "jquery";
export default {
  components: {
    Menu,
    Retour
  },
  mounted() {
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let aside = document.querySelector("aside");
    let second = document.querySelector(".secondImg");
    let third = document.querySelector(".thirdImg");
    let fourth = document.querySelector(".fourthImg");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      first.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      txt.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      if (scroll > 502) {
        scroll = scroll - 502;
        second.style.display = "block";
        third.style.display = "block";
        fourth.style.display = "block";
        aside.style.display = "block";
        second.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        third.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        fourth.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        second.style.display = "none";
        third.style.display = "none";
        fourth.style.display = "none";
        aside.style.display = "none";
      }
    });
  }
};
</script>@