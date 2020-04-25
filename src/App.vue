<template>
  <div id="app">
    <h1>Witaj w systemie zapisów na zajęcia!</h1>
    <div v-if="!logged">
      Zaloguj sie emailem:
    <input type = "email" v-model="email" /><button @click="loginUser()">Wchodzę!</button>
    </div>
    <div v-else>
      Witaj, {{email}} !
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
      }
    }
  }
</script>

<style>

</style>
