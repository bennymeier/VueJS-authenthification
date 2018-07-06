<template>
  <b-container>
    <b-row>
      <b-col>
        <h3>Sign Up</h3>
        <b-alert show variant="danger" v-if="isError">{{ error }}</b-alert>
      </b-col>
    </b-row>
    <b-row>
      <b-col>
        <b-input-group prepend="Username" style="min-width: 70px">
          <b-form-input type="text" v-model="email" placeholder="Email"></b-form-input>
        </b-input-group>
      </b-col>
    </b-row>
    <br>
    <b-row>
      <b-col>
        <b-input-group prepend="Password" style="min-width: 70px">
          <b-form-input type="password" v-model="password" placeholder="Password"></b-form-input>
        </b-input-group>
      </b-col>
    </b-row>
    <br>
    <b-row>
      <b-col>
        <b-button @click="signUp">Sign Up</b-button>
      </b-col>
    </b-row>
    <span>or go back to
      <b-link>
        <router-link to="/login">Login</router-link>
      </b-link>.</span>
  </b-container>
</template>

<script>
import firebase from "firebase";

export default {
  name: "signUp",
  data() {
    return {
      email: "",
      password: "",
      isError: false,
      error: ""
    };
  },
  methods: {
    signUp() {
      firebase
        .auth()
        .createUserWithEmailAndPassword(this.email, this.password)
        .then(
          (user) => {
            this.$router.replace("hello");
          },
          (err) => {
            this.error = `${err.message}`;
            this.isError = true;
          }
        );
    }
  }
};
</script>

<style scoped>
</style>
