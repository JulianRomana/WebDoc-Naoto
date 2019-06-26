<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>{{articleName}}</h1>
      <figure>
        <img :src="articleImage1" alt>
        <figcaption>
          <p>
            10 minutes après le tremblement de Terre, un tsunami eu lieu. Des vagues entre 10 et 15 mètres, atteignant même plus de 30 mètres de haut se sont abattues sur les côtes pacifiques du Japon.
            <br>
            <br>Celles ci se sont étendues jusqu’à 10km dans les villes de Iwate Fukushima et Miyagi, et ont détruit plus de 600km de côtes.
            <br>
            <br>Le tsunami est la cause de plus de 90% des dégâts matériels et des morts. Ce tsunami à aussi provoqué une submersion du système de refroidissement de la centrale de Fukushima .
          </p>
        </figcaption>
      </figure>
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
  background-image: url("../../static/images/seisme/seismeBackground.png");
  background-size: cover;
  background-repeat: no-repeat;
  position: relative;
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
    bottom: 123px;
    right: -310px;
    width: 580px;
    height: 330px;
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
      console.log(response.data);
      this.articleName = response.data[4].name;
      this.articleImage1 = response.data[4].img;
      this.articleImage2 = response.data[4].img2;
      this.articleImage3 = response.data[4].img3;
      this.articleImage4 = response.data[4].img4;
    });
  }
};
</script>@