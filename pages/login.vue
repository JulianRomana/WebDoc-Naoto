<template>
  <div class="screen">
    <form action @submit="checkForm()" method="post">
      <h1>S'identifier</h1>
      <label for="id">Identifiant</label>
      <input class="inputs" v-model="id" type="text" id="id" name="id">
      <label for="password">Mot de passe</label>
      <input class="inputs" v-model="password" type="password" id="password" name="password">
      <input class="button" type="submit" value="Se connecter">
    </form>
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
form {
  position: absolute;
  bottom: 45vh;
  left: 40vw;
  display: flex;
  flex-direction: column;
}
label {
  font-size: 20px;
  color: white;
}
.inputs {
  border-radius: 7px;
  width: 350px;
  height: 30px;
  border: none;
  opacity: 0.6;
  font-size: 16px;
}
.button {
  border-radius: 5px;
  font-size: 20px;
  margin-left: 25%;
  margin-top: 20px;
  height: 40px;
  background-color: #aecc58;
  width: 155px;
  border: none;
  color: white;
}
</style>
<script>
export default {
  data: {
    id: null,
    password: null
  }
};
</script>