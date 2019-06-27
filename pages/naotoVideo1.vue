<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video src="../assets/videos/WebPremierePartie.mp4" width="1450" height="750" autoplay></video>
      <nav class="controls">
        <img class="play-pause" src="../static/images/play.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../static/images/speaker.svg" @click="muteOrUnmute">
      </nav>
    </section>
    <Menu></Menu>
    <nuxt-link class="start" to="./enfantMiracle/enfantMiracle">
      <VoirArticle class="watchArticle"></VoirArticle>
    </nuxt-link>
  </div>
</template>

<script>
import Menu from "~/components/Menu";
import VoirArticle from "~/components/VoirArticle";
export default {
  components: {
    Menu,
    VoirArticle
  },
  mounted: function() {
    const video = document.querySelector("video");
    const seekbar = document.querySelector(".seekbar");

    video.addEventListener("timeupdate", () => {
      seekbar.value = (video.currentTime / video.duration) * seekbar.max;
    });

    seekbar.addEventListener("change", () => {
      video.currentTime = (video.duration * seekbar.value) / seekbar.max;
    });
  },
  methods: {
    playOrPause() {
      const video = document.querySelector("video");
      if (video.paused == true) {
        // Play the video
        video.play();
      } else {
        // Pause the video
        video.pause();
      }
    },
    muteOrUnmute() {
      const video = document.querySelector("video");
      if (video.muted == false) {
        // Mute the video
        video.muted = true;
      } else {
        // Unmute the video
        video.muted = false;
      }
    }
  }
};
</script>

<style scoped lang="scss">
.start {
  color: white;
}
.watchArticle {
  position: fixed;
  top: 40%;
  right: 10px;
}
.firstScreen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 95vh;
  width: 100vw;
  video {
    position: fixed;
    top: 45%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
    width: 100%;
  }
  .controls {
    z-index: 1;
    width: 90%;
    height: 40px;
    background-color: rgba(169, 169, 169, 0.7);
    display: flex;
    justify-content: space-around;
    align-items: center;
    position: absolute;
    bottom: 75px;
    img {
      opacity: 1;
    }
    .seekbar {
      width: 90%;
    }
  }
}
</style>