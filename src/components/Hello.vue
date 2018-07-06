<template>
  <b-container>
    <b-row>
      <b-col>
        <b-alert variant="success" show>Your logged in! </b-alert>
        <br>
        <b-button @click="logout">Logout</b-button>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import firebase from "firebase";

export default {
  name: "hello",
  data() {
    return {
      msg: "Welcome to Your Vue.js App"
    };
  },
  methods: {
    logout() {
      firebase
        .auth()
        .signOut()
        .then(() => {
          this.$router.replace("login");
        });
    }
  }
};
</script>

<style scoped>
</style>
