<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>SEISME SUR LA CÔTE PACIFIQUE DU TOHOKU</h1>
      <figure>
        <img class="firstMove" src="../../static/images/seisme/seisme-1.png" alt />
        <img class="secondImg" src="../../static/images/seisme/seisme-2.png" alt />
        <img class="thirdImg" src="../../static/images/seisme/seisme-3.png" alt />
        <img class="fourthImg" src="../../static/images/seisme/seisme-4.png" alt />
        <figcaption class="txt">
          <p>
            Le 11 mars 2011 à 14h56 (heure française), a lieu un séisme de magnitude 9,1 sur l’échelle de Richter. Le séisme de 2011 de la côte Pacifique du Tohoku frappe les côtes Nord Est de l’île de Honshu (l’île principale du Japon).
            <br />
            <br />Malgré la forte magnitude de cet incident, celui-ci eut peu de répercussions sur les villes avoisinant l’épicentre du séisme grâce aux constructions antisismiques japonaises. Il fait partie des cinq séismes meurtriers les plus puissants.
            <br />
            <br />Ce séisme eut tout de même un impact sur la centrale nucléaire de Fukushima en causant une coupure d’électricité dans la centrale.
          </p>
        </figcaption>
      </figure>
      <aside>
        <h2>177 500</h2>
        <p>Habitants évacués</p>
      </aside>
      <Menu></Menu>
      <nuxt-link class="link" to="../fukushimaArticle/catastrophe">
        <Retour class="returnButton" Retour="Retour"></Retour>
      </nuxt-link>
      <nuxt-link class="link2" to="../tsunami/tsunami">
        <VoirArticle class="next" Article="Suite"></VoirArticle>
      </nuxt-link>
    </section>
  </div>
</template>

<style scoped lang="scss">
.link2 {
  display: none;
}
.next {
  z-index: 4;
  position: fixed;
  top: 40%;
  right: 10px;
  width: 70px;
  height: 70px;
  background-color: white;
  color: black;
  border-radius: 50%;
  text-align: center;
  padding-left: 13px;
  transition: 0.3s ease-in-out;
  cursor: pointer;
  &:hover {
    background-color: rgba(255, 255, 255, 0.561);
  }
}
.singleImage {
  display: none;
}
.fukushima__wrapper {
  width: 100vw;
  height: 180vh;
  background-color: white;
  background-image: url("../../static/images/seisme/seismeBackground.png");
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
    left: 300px;
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
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: fixed;
    bottom: 85px;
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
  color: black;
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
import Menu from "~/components/Menu";
import Retour from "~/components/Retour";
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
    let next = document.querySelector(".link2");
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
        next.style.display = "flex";
        second.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        third.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
        fourth.style.transform = `perspective(500px) translate3d(0, 0, ${scroll}px)`;
      } else {
        second.style.display = "none";
        third.style.display = "none";
        fourth.style.display = "none";
        next.style.display = "none";
        aside.style.display = "none";
      }
    });
  }
};
</script>