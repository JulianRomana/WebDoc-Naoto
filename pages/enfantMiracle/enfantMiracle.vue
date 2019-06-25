<template>
  <div class="enfantMiracle__wrapper">
    <h1>{{arrayName}}</h1>
    <figure>
      <img :src="arrayImage" alt>
      <figcaption>{{arrayContent}}</figcaption>
    </figure>
    <Menu></Menu>
  </div>
</template>


<style scoped lang="scss">
.enfantMiracle__wrapper {
  width: 100vw;
  height: 100vh;
  background-color: white;
  overflow: hidden;
  background-image: url("../../static/images/enfantBG.png");
  background-size: cover;
  background-repeat: no-repeat;
}
figure {
  display: flex;
  height: 80%;
  figcaption {
    background-color: white;
  }
}
h1 {
  text-align: center;
  margin-top: 50px;
  font-size: 20px;
  transition: ease;
}
</style>
<script>
import Menu from "~/components/Menu.vue";
import axios from "axios";
export default {
  data() {
    return {
      arrayName: null,
      arrayContent: null,
      arrayImage: null
    };
  },
  components: {
    Menu
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.arrayName = response.data[2].name;
      this.arrayContent = response.data[2].content;
      this.arrayImage = response.data[2].img;
    });
  }
};
</script>