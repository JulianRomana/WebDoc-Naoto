 <template>
  <div>
 <section id="secondScreen" class="secondScreen">
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
<style lang="scss" scoped>

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
.links {
  font-size: 20px;
  color: black;
  text-decoration: underline;
}
</style>
