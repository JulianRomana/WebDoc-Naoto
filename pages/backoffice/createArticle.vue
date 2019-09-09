<template>
  <div class="form">
    <form @submit="checking" method="post" action>
      <div class="form-group">
        <label for="name">Le nom de l'article</label>
        <input class="form-control" v-model="info.name" id="name" type="text" />
      </div>
      <div class="form-group">
        <label for="content">Le contenu de l'article</label>
        <input
          class="form-control content__input"
          v-model="info.content"
          id="content"
          type="text"
          minlength="50"
        />
      </div>
      <div class="form-group">
        <label for="file">L'image de l'article</label>
        <input class="form-control" v-model="info.img" id="file" type="url" />
      </div>
      <input class="btn btn-primary" type="submit" name="Envoyer" />
    </form>
  </div>
</template>

<style lang="scss" scoped>
.form {
  width: 50vw;
  margin: 0 auto;
}
.content__input {
  height: 100px;
}
</style>
<script>
const axios = require("axios");
export default {
  layout: "articlePage",
  data() {
    return {
      info: {
        name: "",
        content: "",
        img: ""
      },
      id: ""
    };
  },
  mounted() {
    axios
      .get("http://localhost:7892/api/articles")
      .then(response => (this.id = response.data.length));
  },
  methods: {
    checking(e) {
      e.preventDefault();
      axios({
        method: "post",
        url: "http://localhost:7892/api/articles",
        data: {
          name: this.info.name,
          content: this.info.content,
          img: this.info.img,
          id: `${this.id + 1}`
        }
      });
      this.$router.push("/articles/articles");
    }
  }
};
</script>