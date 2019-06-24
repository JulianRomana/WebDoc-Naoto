<template>
  <div class="grid-container">
    <ul class="articles__list">
      <li v-model="article.active" class="article" v-for="article in this.array">
        <h2 class="article__name">{{article.name}}</h2>
        <img class="article__img" :src="article.img" alt>
        <button @click="checking" class="button"></button>
      </li>
    </ul>
  </div>
</template>
