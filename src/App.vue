<template>
  <div id="app">

    <h1>Witaj w systemie zapisów na zajęcia!</h1>

    <div v-if="authenticatedUserName==''">
      <login-form @logged="loginUser($event)"></login-form>
      <!-- <login-form @logged="loginUser($event)" button-label="sss"></login-form> -->
    </div>
    <div v-else>
      <h2>Witaj, {{authenticatedUserName}} !</h2>
      <a @click="logoutUser()">Wyloguj</a>

    </div>

  </div>
</template>

<script>

  import "milligram";
  import LoginForm from "./LoginForm";

  export default {
    components: {LoginForm},
    data() {
      return {
        logged: false,
        authenticatedUserName: ''
      }
    },

    methods: {
      loginUser(username) {
        username = username.trim();
        if(username.length>0) {
          this.authenticatedUserName = username;
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
