<template>
  <div>
    <section id="fukushimaScreen" class="fukushimaScreen">
      <header>
        <div class="title">
          <h1>L’ARCHE DE TOMIOKA</h1>
          <p>NAOTO MASTUMURA : LE GARDIEN DES ANIMAUX</p>
        </div>
        <img class="logo" src="../static/images/logo.png">
      </header>
      <main>
        <h2>FUKUSHIMA</h2>
        <p>Un retour sur le déroulement de la</p>
        <p>catastrophe du 11 Mars 2011</p>
      </main>
      <nav>
        <nuxt-link class="link" to="/apres">
          <div class="previous">
            <p>APRES</p>
          </div>
        </nuxt-link>
        <div class="play">
          <img src="../static/images/line.svg">
          <img src="../static/images/arrow2.svg">
          <p>Commencer l'expèrience</p>
        </div>
        <nuxt-link class="link" to="/naoto">
          <div class="Skip">
            <p>NAOTO MASTUMURA</p>
          </div>
        </nuxt-link>
      </nav>
    </section>
  </div>
</template>
<style scoped lang="scss">
.fukushimaScreen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.541);
  position: absolute;
  z-index: 0;
}
.fukushimaScreen {
  background-image: url("../static/images/fukushima.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  width: 100vw;
}
header {
  display: flex;

  .title {
    color: white;
    font-family: League spartan;
    padding-top: 14px;
    padding-left: 14px;
    z-index: 1;
    h1 {
      font-size: 25px;
    }
    p {
      font-size: 10px;
    }
  }
  .logo {
    width: 200px;
    position: absolute;
    right: 10px;
  }
}
main {
  height: 50%;
  display: flex;
  margin: 0 auto;
  width: 370px;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  color: white;
  font-family: League spartan;

  h2 {
    font-size: 50px;
    z-index: 1;
  }
  p {
    font-size: 20px;
    z-index: 1;
  }
}
nav {
  display: flex;
  justify-content: space-between;
  width: 90%;
  margin-left: 5%;
  color: white;
  font-family: League spartan;

  .previous {
    padding-top: 260px;
    p {
      border-bottom: 1px solid;
    }
  }
  .play {
    display: flex;
    flex-direction: column;
    padding-left: 70px;
    z-index: 1;
    img:nth-child(1) {
      padding-bottom: 20px;
      height: 185px;
    }
    img:nth-child(2) {
      padding-bottom: 10px;
    }
    p {
      border-bottom: 1px solid;
    }
  }
  .Skip {
    padding-top: 260px;
    p {
      border-bottom: 1px solid;
    }
  }
}
.link {
  text-decoration: none;
  color: white;
  z-index: 1;
}
</style>
