<template>
  <div class="screen">
    <FormConnexion></FormConnexion>
  </div>
</template>

<style scoped lang="scss">
h1 {
  text-transform: uppercase;
  color: white;
  text-align: center;
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 100px;
}
.screen {
  width: 100vw;
  height: 100vh;
  background-image: url("/images/loginBackground.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}
.screen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.541);
}
</style>
<script>
import FormConnexion from "../components/Form";

export default {
  components: {
    FormConnexion
  }
};
</script>