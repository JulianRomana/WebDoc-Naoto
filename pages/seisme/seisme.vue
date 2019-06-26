<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>{{articleName}}</h1>
      <figure>
        <img :src="articleImage1" alt>
        <figcaption>
          <p>
            Le 11 mars 2011 à 14h56 (heure française), a lieu un séisme de magnitude 9,1 sur l’échelle de Richter. Le séisme de 2011 de la côte Pacifique du Tohoku frappe les côtes Nord Est de l’île de Honshu (l’île principale du Japon).
            <br>
            <br>Malgré la forte magnitude de cet incident, celui-ci eut peu de répercussions sur les villes avoisinant l’épicentre du séisme grâce aux constructions antisismiques japonaises. Il fait partie des cinq séismes meurtriers les plus puissants.
            <br>
            <br>Ce séisme eut tout de même un impact sur la centrale nucléaire de Fukushima en causant une coupure d’électricité dans la centrale.
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
      this.articleName = response.data[3].name;
      this.articleImage1 = response.data[3].img;
      this.articleImage2 = response.data[3].img2;
      this.articleImage3 = response.data[3].img3;
      this.articleImage4 = response.data[3].img4;
    });
  }
};
</script>