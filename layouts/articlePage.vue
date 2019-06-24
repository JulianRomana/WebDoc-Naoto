<template>
  <div>
    <nav class="navbar navbar-inverse">
      <div class="container-fluid">
        <div class="navbar-header">
          <nuxt-link class="navbar-brand" to="/">Vréel news</nuxt-link>
        </div>
        <ul class="nav navbar-nav">
          <li>
            <nuxt-link class="navbar-brand" to="/articles/articles">Tous les articles</nuxt-link>
          </li>
          <li>
            <nuxt-link class="navbar-brand" to="/articles/createArticle">Créer</nuxt-link>
          </li>
          <li>
            <nuxt-link class="navbar-brand" to="/articles/deleteArticle">Supprimer un article</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
    <nuxt/>
  </div>
</template>

<script>
export default {};
</script>