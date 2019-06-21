<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <div class="byeTitle">
        <h1>FUKUSHIMA</h1>
        <p>NAOTO MATSUMURA : LE GARDIEN DES ANIMAUX</p>
      </div>
      <div class="Skip" v-on:click="nextScreen">
        <img src="../static/images/arrow.svg">
        <p>PASSER L'INTRO</p>
      </div>
      <video src="../assets/videos/intro_webdoc.mp4" autoplay></video>
    </section>
    <section id="secondScreen" class="secondScreen invisible">
      <span>
        {{ msg }}
      </span>
      <div class="Title">
        <h1>NAOTO MATSUMURA</h1>
        <p>20 min</p>
        <p
          class="description"
        >Un webdocumentaire narrant le parcours </br> d’un homme revenu vivre dans son village </br> irradié.</p>
      </div>
      <div class="previous" v-on:click="previousScreen">
        <img src="../static/images/arrow2.svg">
        <p>AVANT</p>
      </div>
      <div class="play">
        <div>
          <img src="../static/images/line.svg">
          <img src="../static/images/arrow2.svg">
        </div>
        <p>Commencer l'expèrience</p>
      </div>
      <div class="Skip">
        <img src="../static/images/arrow2.svg">
        <p>FUKUSHIMA</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {};
</script>

<style scoped lang="scss">
.firstScreen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100vh;
}
.firstScreen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.541);
  position: absolute;
  z-index: -2;
  animation: filterOut 2s forwards;
  animation-delay: 4s;
}
.secondScreen {
  background-image: url("../static/images/pic01.jpg");
  background-size: cover;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;

  span {
    font-family: League spartan;
    position: absolute;
    top: 20px;
    left: 20px;
  }
  .Title {
    z-index: 1;
    font-family: League spartan;
    h1 {
      font-size: 50px;
    }
    p {
      font-family: Roboto;
      font-size: 20px;
    }
  }
}
.secondScreen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.541);
  position: absolute;
  z-index: 0;
}
.invisible {
  display: none;
}
.byeTitle {
  z-index: 1;
  position: absolute;
  right: 10vw;
  top: 300px;
  font-family: League spartan;
  color: white;
  animation: filterOut 2s forwards;
  animation-delay: 4s;
  h1 {
    font-size: 90px;
  }
  p {
    font-size: 22px;
  }
}
.Skip {
  z-index: 1;
  color: white;
  font-family: League spartan;
  position: absolute;
  bottom: 5%;
  right: 5%;
  display: flex;
  justify-content: center;
  align-items: center;

  img {
    padding-right: 25px;
  }
}
.previous {
  z-index: 1;
  color: white;
  font-family: League spartan;
  position: absolute;
  bottom: 5%;
  left: 5%;
  display: flex;
  justify-content: center;
  align-items: center;

  img {
    padding-right: 25px;
  }
}
.play {
  z-index: 1;
  position: absolute;
  bottom: 5%;
  display: flex;
  flex-direction: row;
  align-items: flex-end;
  font-family: RobotoMedium;
  padding-left: 6%; 

  div {
  display: flex;
  flex-direction: column;
  }
  p {
    padding-bottom: 18px;
    padding-left: 20px;
  }
  img:nth-child(1) {
    padding-bottom: 20px;
    height: 180px;
  }
}
video {
  position: fixed;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
  transform: translateX(-50%) translateY(-50%);
  z-index: -3;
}
.links {
  font-size: 20px;
  color: black;
  text-decoration: underline;
}
@keyframes filterOut {
  from {
    opacity: 1;
  }

  to {
    opacity: 0;
  }
}
</style>
<script>
export default {
  data: function() {
    return {
    invisible: false,
    msg: "L'ARCHE DE TOMIOKA"
    }
  },
  methods: {
    nextScreen() {
      let screen = document.getElementById("firstScreen");
      let screen2 = document.getElementById("secondScreen");
      screen.classList.add("invisible");
      screen2.classList.remove("invisible");
    },
    previousScreen() {
      let screen = document.getElementById("secondScreen");
      let screen2 = document.getElementById("firstScreen");
      screen.classList.add("invisible");
      screen2.classList.remove("invisible");
      console.log("lourd")
    }
  }
};
</script>
