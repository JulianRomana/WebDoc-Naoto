<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>{{articleName}}</h1>
      <figure>
        <img class="firstMove" :src="articleImage1" alt>
        <img class="secondImg" :src="articleImage2" alt>
        <img class="thirdImg" :src="articleImage3" alt>
        <img class="fourthImg" :src="articleImage4" alt>
        <figcaption class="txt">
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
      <Menu></Menu>
      <nuxt-link class="return" to="fukushimaVideo">
        <Retour class="returnButton"></Retour>
      </nuxt-link>
    </section>
  </div>
</template>

<style scoped lang="scss">
.return {
  color: black;
}
.singleImage {
  display: none;
}
.fukushima__wrapper {
  width: 100vw;
  height: 265vh;
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
    box-shadow: 0px 0px 4px 0px #656565;
    border: none;
    position: fixed;
    bottom: 69px;
    right: 330px;
    width: 580px;
    height: 385px;
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
  head: {
    script: [
      {
        src: "https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.min.js"
      }
    ]
  },
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
      this.articleName = response.data[1].name;
      this.articleImage1 = response.data[1].img;
      this.articleImage2 = response.data[1].img2;
      this.articleImage3 = response.data[1].img3;
      this.articleImage4 = response.data[1].img4;
    });
    let first = document.querySelector(".firstMove");
    let txt = document.querySelector(".txt");
    let aside = document.querySelector("aside");
    let second = document.querySelector(".secondImg");
    let third = document.querySelector(".thirdImg");
    let fourth = document.querySelector(".fourthImg");
    $(window).scroll(function(event) {
      let scroll = $(window).scrollTop();
      let scrollDiv = scroll / 100;
      let scrollSecond = scrollDiv - 3;
      console.log(scrollDiv);
      first.style.transform = `scale(${1 + scrollDiv})`;
      txt.style.transform = `scale(${1 + scrollDiv})`;
      let size = 3.2;
      if (scrollDiv > size) {
        first.style.display = "none";
        txt.style.display = "none";
        aside.style.display = "none";
        second.style.display = "block";
        second.style.transform = `scale(${scrollSecond})`;
        if (scrollSecond > size) {
          second.style.display = "none";
          third.style.display = "block";
          scrollSecond = scrollSecond - 2.6;
          third.style.transform = `scale(${scrollSecond})`;
          if (scrollSecond > size) {
            third.style.display = "none";
            fourth.style.display = "block";
            scrollSecond = scrollSecond - 2.6;
            fourth.style.transform = `scale(${scrollSecond})`;
            if (scrollSecond > size) {
              fourth.style.display = "none";
            }
          }
        }
      } else {
        first.style.display = "block";
        txt.style.display = "block";
        aside.style.display = "block";
        second.style.display = "none";
        third.style.display = "none";
        fourth.style.display = "none";
      }
    });
  }
};
</script>