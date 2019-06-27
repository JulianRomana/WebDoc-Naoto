<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video src="../../assets/videos/apres1.mp4" width="1450" height="750" autoplay></video>
      <nav class="controls">
        <img class="play-pause" src="../../static/images/play.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../../static/images/speaker.svg" @click="muteOrUnmute">
      </nav>
    </section>
    <nuxt-link to="article2" class="nav">voir l'article</nuxt-link>
    <Menu></Menu>
  </div>
</template>

<script>
import Menu from "~/components/Menu";
export default {
  components: {
    Menu
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