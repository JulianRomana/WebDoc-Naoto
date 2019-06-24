<template>
  <div class="screen">
    <div class="content">
      <h1>S'identifier</h1>
      <FormConnexion></FormConnexion>
    </div>
  </div>
</template>

<style scoped lang="scss">
h1 {
  text-transform: uppercase;
  color: white;
  text-align: center;
  font-size: 30px;
  font-weight: bold;
  padding-top: 30px;
  margin-bottom: 50px;
  z-index: 3;
}
.screen {
  width: 100vw;
  height: 100vh;
  background-image: url("/images/loginBackground.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  display: flex;
  align-items: center;
  flex-direction: column;
}
.content {
  margin-top: 200px;
  z-index: 2;
}
.screen::before {
  content: "";
  display: block;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.541);
  position: absolute;
  z-index: 2;
}
</style>
<script>
import FormConnexion from "~/components/Form";
const axios = require("axios");

export default {
  data() {
    return {
      array: null
    };
  },
  components: {
    FormConnexion
  }
};
</script>