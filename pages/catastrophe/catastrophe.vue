<template>
  <div class="fukushima__wrapper">
    <section class="content">
      <h1>{{articleName}}</h1>
      <figure>
        <img :src="articleImage1" alt>
        <figcaption>{{articleContent}}</figcaption>
      </figure>
      <Menu></Menu>
      <Retour></Retour>
    </section>
  </div>
</template>

<style scoped lang="scss">
.fukushima__wrapper {
  width: 100vw;
  heig
}
</style>
<script>
import Menu from "~/components/Menu.vue";
import axios from "axios";
import Retour from "~/components/Retour.vue";
export default {
  data() {
    return {
      articleName: null,
      articleContent: null,
      articleImage1: null,
      articleImage2: null,
      articleImage3: null,
      articleImage4: null
    };
  },
  components: {
    Menu,
    Retour
  },
  mounted() {
    axios.get("http://localhost:7892/api/articles").then(response => {
      this.articleName = response.data[1].name;
      this.articleContent = response.data[1].content;
      this.articleImage1 = response.data[1].img;
      this.articleImage2 = response.data[1].img2;
      this.articleImage3 = response.data[1].img3;
      this.articleImage4 = response.data[1].img4;
    });
  }
};
</script>