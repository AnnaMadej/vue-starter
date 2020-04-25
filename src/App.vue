<template>
  <div id="app">
    <h1>Witaj w systemie zapisów na zajęcia!</h1>
    <div v-if="!logged">
      Zaloguj sie emailem:
    <input type = "text" v-model="email" /><button @click="loginUser()">Wchodzę!</button>
    </div>
    <div v-else>
      <h2>Witaj, {{email}} !</h2>
      <p @click="logoutUser()">Wyloguj!</p>

    </div>

  </div>
</template>

<script>

  import "milligram";

  export default {
    data() {
      return {
        logged: false,
        email: ''
      }
    },

    methods: {
      alertMyEmail() {
        alert(this.email);
      },
      loginUser() {
        this.logged = true;
      },
      logoutUser() {
        this.logged = false;
      }
    }
  }
</script>

<style>

</style>
