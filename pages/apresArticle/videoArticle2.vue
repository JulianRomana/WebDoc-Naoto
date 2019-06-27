<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video
        src="../../assets/videos/apres2.mp4"
        width="1450"
        height="750"
        autoplay
        @mouseover="hideSeekBar"
      ></video>
      <nav class="controls">
        <img class="play-pause" src="../../static/images/play.svg" @click="playOrPause">
        <img class="pause-play" src="../../static/images/pause.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../../static/images/speaker.svg" @click="muteOrUnmute">
        <img class="unmute" src="../../static/images/speakerMute.svg" @click="muteOrUnmute">
      </nav>
    </section>
    <Menu></Menu>
    <nuxt-link class="start" to="article1">
      <Retour Retour="Retour Article" class="returnButton">Retour Article</Retour>
    </nuxt-link>
    <nuxt-link class="start" to="article2">
      <VoirArticle Article="Article Suivant" class="watchArticle"></VoirArticle>
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
    hideSeekBar() {
      const nav = document.querySelector("nav");
      nav.style.display = "flex";
      setTimeout(() => {
        nav.style.display = "none";
      }, 5000);
    },
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
        button.style.display = "flex";
        button2.style.display = "none";
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
.returnButton {
  position: fixed;
  top: 40%;
  left: 10px;
  width: 70px;
  height: 70px;
  color: black;
  background-color: rgba(255, 255, 255, 0.561);
  border-radius: 50%;
  text-align: center;
  transition: 0.3s ease-in-out;
  font-weight: bold;
  cursor: pointer;
  color: white;
  p {
    padding-top: 21px;
  }
  &:hover {
    background-color: black;
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
    animation: Hide 1s;

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
@keyframes Hide {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>