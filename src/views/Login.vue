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
    <input type="text" v-model="login.password" />
  </div>
  <button v-on:click="LogmeIn()">Login</button>
</template>
