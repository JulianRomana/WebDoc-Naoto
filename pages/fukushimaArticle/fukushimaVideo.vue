<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video src="../../assets/videos/Fukushima.mp4" width="1450" height="750" autoplay></video>
      <nav class="controls">
        <img class="play-pause" src="../../static/images/play.svg" @click="playOrPause">
        <img class="pause-play" src="../../static/images/pause.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../../static/images/speaker.svg" @click="muteOrUnmute">
        <img class="unmute" src="../../static/images/speakerMute.svg" @click="muteOrUnmute">
      </nav>
    </section>
    <nuxt-link class="start" to="catastrophe">
      <VoirArticle Article="Voir l'Article"></VoirArticle>
    </nuxt-link>
    <Menu></Menu>
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
      let button = document.querySelector(".play-pause");
      let button2 = document.querySelector(".pause-play");
      if (video.paused == true) {
        // Play the video
        video.play();
        button.style.display = "none";
        button2.style.display = "flex";
      } else {
        // Pause the video
        video.pause();
        button.style.display = "none";
        button2.style.display = "flex";
      }
    },
    muteOrUnmute() {
      const video = document.querySelector("video");
      let button = document.querySelector(".mute");
      let button2 = document.querySelector(".unmute");
      if (video.muted == false) {
        // Mute the video
        video.muted = true;
        button.style.display = "none";
        button2.style.display = "flex";
      } else {
        // Unmute the video
        video.muted = false;
        button.style.display = "flex";
        button2.style.display = "none";
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
    bottom: 76px;
    img {
      opacity: 1;
    }
    .seekbar {
      width: 90%;
    }
    .play-pause {
      display: none;
    }
    .unmute {
      display: none;
    }
  }
}
.start {
  position: fixed;
  top: 40%;
  right: 10px;
}
</style>