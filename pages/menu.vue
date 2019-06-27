<template>
  <div>
    <section id="menuScreen" class="menuScreen">
      <img class="logo" src="../static/images/logo.png">
      <div class="menuTitle">
        <h1>L’ARCHE DE TOMIOKA</h1>
        <p>NAOTO MASTUMURA : LE GARDIEN DES ANIMAUX</p>
      </div>
      <ul>
        <nuxt-link class="link" to="/fukushima">
          <li>FUKUSHIMA</li>
        </nuxt-link>
        <nuxt-link class="link" to="/naoto">
          <li class="mainArticle">NAOTO MATSUMURA</li>
        </nuxt-link>
        <nuxt-link class="link" to="/apres">
          <li>L'APRES</li>
        </nuxt-link>
      </ul>
    </section>
    <audio :src="require('@/assets/audio/cigales.mp3')" autoplay></audio>
  </div>
</template>
<style scoped lang="scss">
.mainArticle {
  font-size: 20px;
  &:hover {
    font-size: 22px;
    &::before {
      content: "";
      display: block;
      width: 0%;
      height: 2px;
      position: absolute;
      bottom: 0;
      background-color: white;
      animation: 0.4s beforeAnimation linear forwards;
    }
  }
}
.menuScreen {
  background-image: url("../static/images/menuFond.jpg");
  background-size: cover;
  background-position: center;
  height: 100vh;
  width: 100vw;
  .logo {
    width: 200px;
    position: absolute;
    right: 10px;
  }
  .menuTitle {
    position: absolute;
    left: 1vw;
    top: 150px;
    font-family: League spartan;
    color: white;
    h1 {
      font-size: 80px;
    }
    p {
      font-size: 28px;
    }
  }
  ul {
    text-align: center;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    position: absolute;
    left: 5%;
    bottom: 20px;
    width: 90%;
    color: white;
    font-family: League spartan;
    li {
      color: white;
      position: relative;
      transition: 0.4s;
      &:hover:not(.mainArticle) {
        &::before {
          content: "";
          display: block;
          width: 0%;
          height: 2px;
          position: absolute;
          bottom: 0;
          background-color: white;
          animation: 0.4s beforeAnimation linear forwards;
        }
      }
    }
  }
}
.link {
  text-decoration: none;
  color: white;
}
@keyframes beforeAnimation {
  0% {
    width: 0%;
  }
  100% {
    width: 100%;
  }
}
</style>
<script>
export default {};
</script>
