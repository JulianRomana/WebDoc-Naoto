<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>{{articleName}}</h1>
      <figure>
        <img :src="articleImage1" alt>
        <figcaption>
          <p>
            Suite au tremblement de terre qui a causé une panne d’électricité, et au tsunami qui a submergé la centrale puis mis hors service le système de refroidissement des réacteurs, les réacteurs 1,2 et 3 sont entrés en fusion, ce qui a causé plusieurs explosions a l’intérieur de la centrale sur plusieurs jours.
            <br>
            <br>Cet incident nucléaire est un accident de niveau 7 sur l’échelle de Richter, et équivaut à celui de Tchernobyl.
            <br>
            <br>Dès les premiers jours et encore aujourd’hui, d'importants rejets sont dispersés dans l'air. Ils se déplacent au gré des vent, et en raison de fuites continues, les rejets touches le littoral proche, les fonds marins et l’Océan Pacifique.
          </p>
        </figcaption>
      </figure>
      <aside>
        <h2>216 Md</h2>
        <p>D'Euros de dégats</p>
      </aside>
      <img class="singleImage" :src="articleImage2" alt>
      <img class="singleImage" :src="articleImage3" alt>
      <img class="singleImage" :src="articleImage4" alt>
      <Menu></Menu>
      <Retour class="returnButton"></Retour>
    </section>
  </div>
</template>

<style scoped lang="scss">
.singleImage {
  display: none;
}
.fukushima__wrapper {
  width: 100vw;
  height: 100vh;
  background-color: white;
  background-image: url("../../static/images/catastrophe/blurryFukushima.png");
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
}
aside {
  position: absolute;
  right: 100px;
  top: 30%;
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
  img {
    position: absolute;
    top: 0;
    left: 150px;
    z-index: 1;
  }
  figcaption {
    background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: absolute;
    z-index: 2;
    bottom: 25px;
    right: -140px;
    width: 580px;
    height: 385px;
    font-size: 18px;
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
  text-align: left;
  margin-left: 150px;
  padding: 50px 0px 50px;
  font-size: 20px;
}
.returnButton {
  position: absolute;
  top: 45%;
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
import axios from "axios";
import Retour from "~/components/Retour.vue";
export default {
  data() {
    return {
      articleName: null,
      articleContent: null,
      articleImage1: null,
      articleImage2: null,
      articleImage3: null,
      articleImage4: null
    };
  },
  components: {
    Menu,
    Retour
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.articleName = response.data[1].name;
      this.articleContent = response.data[1].content;
      this.articleImage1 = response.data[1].img;
      this.articleImage2 = response.data[1].img2;
      this.articleImage3 = response.data[1].img3;
      this.articleImage4 = response.data[1].img4;
    });
  }
};
</script>