<template>
  <div>
    <h1> System do zapisów na zajęcia</h1>
    <div v-show="loggedUser">
      <user-panel @logout="logMeOut()" :userName="loggedUser"/>
      <meeting-page :loggedUser="loggedUser"/>
    </div>
    <div v-if="!loggedUser">
      <login-form @login="logMeIn($event)" v-if="!loggedUser"/>
    </div>
  </div>

</template>

<script>
  import "milligram";
  import MeetingPage from "./meetings/MeetingPage";
  import LoginForm from "./LoginForm";
  import UserPanel from "./UserPanel";


  export default {

    components: {UserPanel, LoginForm, MeetingPage},
    data() {
      return {
        loggedUser: ''
      }
    },
    methods: {
      logMeIn(userName) {
        if (userName != null) {
          this.loggedUser = userName;
        }
      },
      logMeOut() {
        if (this.loggedUser != null) {
          this.loggedUser = '';
        }
      }
    }
  }

</script>

<style>

</style>
