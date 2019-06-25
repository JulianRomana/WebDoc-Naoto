
<template>
  <div class="return__button">
    <p>Retour</p>
  </div>
</template>

<style scoped lang="scss">
.return__button {
  width: 70px;
  height: 70px;
  background-color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  text-align: center;
  &::before {
    content: "<-";
    display: block;
  }
}
</style>
<script>
export default {
  props: ["Retour"]
};
</script>