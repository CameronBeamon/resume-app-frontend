<script>
import axios from "axios";

export default {
  data: function () {
    return {
      Username: "",
      Password: "",
    };
  },
  methods: {
    LogmeIn: function () {
      axios.post("https://fierce-cove-12825.herokuapp.com/sessions", this.Username, this.Password).then((response) => {
        console.log(response.data);
      });
    },
  },
};
</script>

<template>
  <div>
    <p>Username:</p>
    <input type="text" v-model="Username" />
  </div>
  <div>
    <p>Password:</p>
    <input type="text" v-model="Password" />
  </div>
  <button v-on:click="LogmeIn()">Login</button>
</template>
