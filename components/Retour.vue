
<template>
  <div class="return__button">
    <p>Video</p>
  </div>
</template>

<style scoped lang="scss">
.return__button {
  width: 70px;
  height: 70px;
  background-color: white;
  border-radius: 50%;
  text-align: center;
  transition: 0.3s ease-in-out;
  cursor: pointer;
  p {
    font-weight: bold;
    padding-top: 25px;
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