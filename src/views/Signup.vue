<script>
import axios from "axios";

export default {
  data: function () {
    return {
      signUp: {},
    };
  },
  methods: {
    signMeUp: function () {
      axios.post("https://fierce-cove-12825.herokuapp.com/students", this.signUp).then((response) => {
        console.log(response.data);
      });
    },
  },
};
</script>

<template>
  <div>
    <p>Email:</p>
    <input type="text" v-model="signUp.email" />
  </div>
  <div>
    <p>Password:</p>
    <input type="password" v-model="signUp.password" />
  </div>
  <button v-on:click="signMeUp()">Signup</button>
</template>
