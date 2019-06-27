<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <div class="Title">
        <h1>L’ARCHE DE TOMIOKA</h1>
        <p>NAOTO MASTUMURA : LE GARDIEN DES ANIMAUX</p>
      </div>
      <nuxt-link class="Skip" to="/menu">
        <img src="../static/images/arrow.svg">
        <p>PASSER L'INTRO</p>
      </nuxt-link>
      <video src="../assets/videos/intro_webdoc.mp4" autoplay></video>
    </section>
  </div>
</template>

<script>
export default {
  mounted() {
    setTimeout(() => {
      this.$router.push("/menu");
    }, 32000);
  }
};
</script>

<style scoped lang="scss">
.firstScreen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100vh;
  .Title {
    z-index: 1;
    position: absolute;
    left: 1vw;
    top: 150px;
    font-family: League spartan;
    color: white;
    animation: filterOut 2s forwards;
    animation-delay: 4s;
    h1 {
      font-size: 80px;
    }
    p {
      font-size: 28px;
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
    text-decoration: none;

    img {
      padding-right: 25px;
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
@keyframes filterOut {
  from {
    opacity: 1;
  }

  to {
    opacity: 0;
  }
}
</style>