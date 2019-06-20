<template>
  <div class="screen">
    <div class="Title">
      <h1>FUKUSHIMA</h1>
      <p>NAOTO MATSUMURA : LE GARDIEN DES ANIMAUX</p>
    </div>
    <div class="Skip">
      <nuxt-link class="nuxt-links" to="/page2">
        <img src="../static/images/arrow.svg">
        <p>PASSER L'INTRO</p>
      </nuxt-link>
    </div>
    <video src="../assets/videos/intro_webdoc.mp4" autoplay></video>
  </div>
</template>

<script>
export default {};
</script>

<style scoped lang="scss">
.screen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100vh;
}
.screen::before {
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
.Title {
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

  .nuxt-links {
    color: white;
    text-decoration: none;
    display: flex;
    justify-content: center;
    align-items: center;
    p {
      font-size: 16px;
    }
  }
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
