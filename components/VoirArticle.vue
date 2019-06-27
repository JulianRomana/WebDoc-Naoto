
<template>
  <div class="see__article">
    <p>Voir l'article</p>
  </div>
</template>

<style scoped lang="scss">
.see__article {
  width: 70px;
  height: 70px;
  background-color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  text-align: center;
  transition: 0.3s ease-in-out;
  cursor: pointer;
  p {
    font-weight: bold;
    text-align: center;
  }
  &:hover {
    background-color: rgba(255, 255, 255, 0.561);
  }
}
</style>
<script>
export default {
  props: ["VoirArticle"]
};
</script>