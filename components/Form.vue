<template>
  <form id="form" action @submit="checkForm" method="post">
    <label for="id">Identifiant</label>
    <input v-model="id" class="inputs" type="text" id="id" name="id">
    <label for="password">Mot de passe</label>
    <input v-model="password" class="inputs" type="password" id="password" name="password">
    <input class="button" type="submit" value="Se connecter">
  </form>
</template>
<style scoped lang="scss">
form {
  display: flex;
  flex-direction: column;
}
label {
  font-size: 20px;
  color: white;
  margin-top: 10px;
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
  },
  methods: {
    checkForm: e => {
      e.preventDefault();
      if (id.value === "admin" && password.value === "admin") {
      }
    }
  },
  mounted() {
    console.log(id, password);
  }
};
</script>