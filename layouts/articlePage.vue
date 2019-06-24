<template>
  <div>
    <nav class="navbar navbar-inverse">
      <div class="container-fluid">
        <div class="navbar-header">
          <nuxt-link class="navbar-brand" to="/">Vréel news</nuxt-link>
        </div>
        <ul class="nav navbar-nav">
          <li class="active">
            <a to="/articles/articles">Articles</a>
          </li>
          <li>
            <nuxt-link class="navbar-brand" to="/articles/createArticle">Créer</nuxt-link>
          </li>
          <li>
            <nuxt-link class="navbar-brand" to="/articles/deleteArticle">Supprimer un article</nuxt-link>
          </li>
          <li>
            <a href="#">Page 3</a>
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