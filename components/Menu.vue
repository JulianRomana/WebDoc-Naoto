<template>
  <div class="menu__wrapper">
    <nav class="menu">
      <ul class="menu__list">
        <li class="menu__item firstElement">MENU</li>
        <li>
          <nuxt-link to="/menu" class="menu__item">Accueil</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/fukushima" class="menu__item">FUKUSHIMA</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/naoto" class="menu__item">NAOTO MATSUMURA</nuxt-link>
        </li>
        <li>
          <nuxt-link to="/apres" class="menu__item">L'APRES</nuxt-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<style scoped lang="scss">
.menu__wrapper {
  position: fixed;
  bottom: 0;
  width: 100vw;
}

.menu__item:not(.firstElement) {
  opacity: 0;
}
.menu__item {
  color: white;
  transition: 0.1s linear;
  font-family: League spartan;
  text-transform: uppercase;
  cursor: pointer;
  &:hover {
    color: rgba(255, 255, 255, 0.705);
  }
}
.menu__list {
  position: relative;
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 100%;
}
.menu {
  background-color: black;
  transition: 0.3s;
  width: 100%;
  height: 30px;
  align-self: center;
  &:hover {
    height: 60px;
    .menu__item:not(.firstElement) {
      animation: menuFade 0.5s linear forwards;
    }
    .firstElement {
      transform: translateX(-200px);
      display: none;
    }
  }
}
.firstElement {
  transition: 0.5 linear;
}
@keyframes menuFade {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 0.5;
  }
  100% {
    opacity: 1;
  }
}
</style>

<script>
export default {
  props: ["Menu"]
};
</script>