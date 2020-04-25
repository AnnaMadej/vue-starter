<template>
  <div id="app">
    <h1>Witaj w systemie zapisów na zajęcia!</h1>
    <div v-if="authenticatedUserName==''">
      Zaloguj sie emailem:
      <input type = "text" v-model="email" /><button @click="loginUser()">Wchodzę!</button>
    </div>
    <div v-else>
      <h2>Witaj, {{authenticatedUserName}} !</h2>
      <a @click="logoutUser()">Wyloguj</a>

    </div>

  </div>
</template>

<script>

  import "milligram";

  export default {
    data() {
      return {
        logged: false,
        email: '',
        authenticatedUserName: ''
      }
    },

    methods: {
      alertMyEmail() {
        alert(this.email);
      },
      loginUser() {
        this.email = this.email.trim();
        if(this.email.length>0) {
          this.authenticatedUserName = this.email;
          this.email = '';
        }
      },
      logoutUser() {
        this.authenticatedUserName = '';
      }
    }
  }
</script>

<style>

</style>
