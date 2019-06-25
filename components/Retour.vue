
<template>
  <div class="return__button">
    <p>VIDEO</p>
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
  transition: 0.3s ease-in-out;
  cursor: pointer;
  &::before {
    content: "◀";
    display: block;
  }
  p {
    font-weight: bold;
  }
  &:hover {
    background-color: rgba(255, 255, 255, 0.561);
  }
}
</style>
<script>
export default {
  props: ["Retour"]
};
</script>