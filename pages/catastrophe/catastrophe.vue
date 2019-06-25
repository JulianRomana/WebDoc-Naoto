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
      <Menu></Menu>
      <Retour></Retour>
    </section>
  </div>
</template>

<style scoped lang="scss">
.fukushima__wrapper {
  width: 100vw;
  height: 100vh;
  background-color: white;
  background-image: url("../../static/images/catastrophe/blurryFukushima.png");
  background-size: cover;
  background-repeat: no-repeat;
}
.content {
  height: 80%;
  width: 100%;
}
figure {
  position: relative;
  width: 1000px;
  height: 100%;
  img {
    position: absolute;
    top: 0;
    left: 200px;
    z-index: 1;
  }
  figcaption {
    background-color: rgb(255, 255, 255);
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: absolute;
    z-index: 2;
    bottom: 70px;
    right: -90px;
    width: 590px;
    font-size: 18px;
    &::first-line {
      font-weight: bold;
    }
    p {
      margin: 20px 20px 0px 20px;
      line-height: 1.6rem;
    }
  }
}
h1 {
  text-align: left;
  margin-left: 200px;
  padding: 50px 0px 50px;
  font-size: 20px;
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