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
          <li>NAOTO MATSUMURA</li>
        </nuxt-link>
        <nuxt-link class="link" to="/apres">
          <li>APRES</li>
        </nuxt-link>
      </ul>
    </section>
  </div>
</template>
<style scoped lang="scss">
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
      border-bottom: 1px solid;
    }
  }
}
.link {
  text-decoration: none;
  color: white;
}
</style>
<script>
export default {};
</script>
