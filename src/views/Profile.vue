<script>
import axios from "axios";

export default {
  data: function () {
    return {
      profile: {},
    };
  },
  created: function () {
    axios.get("https://fierce-cove-12825.herokuapp.com/students/4").then((response) => {
      this.profile = response.data;
    });
    console.log("looks like it's working");
  },
  methods: {},
};
</script>

<template>
  <div class="profile">
    <img v-bind:src="profile.photo_url" />
    <h2>Check out your beautiful profile!</h2>
    <p>Name: {{ profile.first_name + " " + profile.last_name }}</p>
    <p>Email Address: {{ profile.email }}</p>
    <p>Phone Number: {{ profile.phone_number }}</p>
    <p>Short Bio: {{ profile.short_bio }}</p>
    <p>Linkedin: {{ profile.linkedin_url }}</p>
    <p>Personal Blog: {{ profile.personal_blog_url }}</p>
    <p>Resume: {{ profile.resume_url }}</p>
    <p>Github: {{ profile.github_url }}</p>
    <p>Twitter: {{ profile.twitter_handle }}</p>
  </div>
</template>
