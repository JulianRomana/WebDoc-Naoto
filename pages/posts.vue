<template>
  <div class="posts">
    <h1>Posts</h1>
    <nuxt-link class="nuxt-links" to="/">Retour à l'accueil</nuxt-link>
  </div>
</template>

<style scoped lang="scss">
.posts {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 50vh;
}
h1 {
  text-align: center;
  font-size: 36px;
  font-family: sans-serif;
}
</style>