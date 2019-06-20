<template>
  <form id="form" action @submit="checkForm()" method="post">
    <h1>S'identifier</h1>
    <label for="id">Identifiant</label>
    <input v-model="id" class="inputs" type="text" id="id" name="id">
    <label for="password">Mot de passe</label>
    <input v-model="password" class="inputs" type="password" id="password" name="password">
    <input class="button" type="submit" value="Se connecter">
  </form>
</template>
<style>
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
  props: ["FormConnexion"],
  data() {
    return {
      id: null,
      password: null
    };
  }
};
</script>