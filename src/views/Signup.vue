<script>
export default {
  data: function () {
    return {
      Username: "",
      Password: "",
      conPassword: "",
    };
  },
  methods: {
    signMeUp: function () {
      console.log("hi");
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
  <div>
    <p>Confirm Password:</p>
    <input type="text" v-model="Password" />
  </div>
  <button v-on:click="signMeUp()">Signup</button>
</template>
