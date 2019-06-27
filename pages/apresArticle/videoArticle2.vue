<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video src="../../assets/videos/apres2.mp4" width="1450" height="750" autoplay></video>
      <nav class="controls">
        <img class="play-pause" src="../../static/images/play.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../../static/images/speaker.svg" @click="muteOrUnmute">
      </nav>
    </section>
    <Menu></Menu>
    <nuxt-link class="start" to="article2">
      <VoirArticle class="watchArticle"></VoirArticle>
    </nuxt-link>
    <nuxt-link class="start" to="article1">
      <span class="returnButton">Retour article</span>
    </nuxt-link>
  </div>
</template>

<script>
import Menu from "~/components/Menu";
import VoirArticle from "~/components/VoirArticle";
import Retour from "~~/components/Retour";
export default {
  components: {
    Menu,
    VoirArticle,
    Retour
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
.returnButton {
  position: fixed;
  top: 300px;
  left: 0;
  width: 70px;
  height: 70px;
  color: black;
  background-color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  text-align: center;
  transition: 0.3s ease-in-out;
  cursor: pointer;
  &::before {
    content: "◀";
    display: block;
  }
  p {
    font-weight: bold;
  }
  &:hover {
    background-color: rgba(255, 255, 255, 0.561);
  }
}
.firstScreen {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 90vh;
  video {
    position: fixed;
    top: 45%;
    left: 50%;
    transform: translateX(-50%) translateY(-50%);
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
    bottom: 50px;

    img {
      opacity: 1;
    }
    .seekbar {
      width: 90%;
    }
  }
}
</style>