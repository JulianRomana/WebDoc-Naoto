
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
    animation: innerImage 0.3s forwards;
    p {
      display: none;
    }
    &::before {
      display: none;
    }
  }
}
@keyframes innerImage {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
    background-image: url("../static/images/fukushima.png");
    background-size: cover;
    background-repeat: no-repeat;
  }
}
</style>
<script>
export default {
  props: ["Retour"]
};
</script>