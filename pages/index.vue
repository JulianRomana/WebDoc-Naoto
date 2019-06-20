<template>
  <div class="screen">
    <h1>Accueil</h1>
    <nuxt-link class="nuxt-links" to="/posts">Voir les posts</nuxt-link>
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
  height: 50vh;
}
h1 {
  text-align: center;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 36px;
}
.links {
  font-size: 20px;
  color: black;
  text-decoration: underline;
}
</style>
