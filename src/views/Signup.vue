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
    <p>Username:</p>
    <input type="text" v-model="singUp.username" />
  </div>
  <div>
    <p>Password:</p>
    <input type="text" v-model="singUp.password" />
  </div>
  <div>
    <p>Confirm Password:</p>
    <input type="text" v-model="singUp.confirm_password" />
  </div>
  <button v-on:click="signMeUp()">Signup</button>
</template>
