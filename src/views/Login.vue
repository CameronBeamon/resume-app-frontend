<script>
import axios from "axios";

export default {
  data: function () {
    return {
      login: {},
    };
  },
  methods: {
    LogmeIn: function () {
      axios.post("https://fierce-cove-12825.herokuapp.com/sessions", this.login).then((response) => {
        console.log(response.data);
        axios.defaults.headers.common["Authorization"] = "Bearer " + response.data.jwt;
        localStorage.setItem("jwt", response.data.jwt);
        localStorage.setItem("student_id", response.data.student_id);
        this.$router.push("/profile");
      });
    },
  },
};
</script>

<template>
  <div>
    <p>Username:</p>
    <input type="text" v-model="login.email" />
  </div>
  <div>
    <p>Password:</p>
    <input type="password" v-model="login.password" />
  </div>
  <button v-on:click="LogmeIn()">Login</button>
</template>
