<template>
  <div>
    <section id="firstScreen" class="firstScreen">
      <video
        src="../assets/videos/WebDeuxiemePartie.mp4"
        width="1450"
        height="750"
        autoplay
        @mouseover="hideSeekBar"
      ></video>
      <nav class="controls">
        <img class="play-pause" src="../static/images/play.svg" @click="playOrPause">
        <img class="pause-play" src="../static/images/pause.svg" @click="playOrPause">
        <input class="seekbar" type="range" min="0" max="100">
        <img class="mute" src="../static/images/speaker.svg" @click="muteOrUnmute">
        <img class="unmute" src="../static/images/speakerMute.svg" @click="muteOrUnmute">
      </nav>
    </section>
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
    display: none;
    justify-content: space-around;
    align-items: center;
    position: absolute;
    bottom: 75px;
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