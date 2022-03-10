<script>
import axios from "axios";
export default {
  data: function () {
    return {
      profile: {},
      editProfileParams: {},
      errors: [],
    };
  },
  created: function () {
    axios.get("https://fierce-cove-12825.herokuapp.com/students/" + localStorage.student_id).then((response) => {
      this.profile = response.data;
    });
    console.log("looks like it's working");
  },
  methods: {
    updateProfile: function () {
      axios
        .patch("https://fierce-cove-12825.herokuapp.com/students/" + localStorage.student_id, this.editProfileParams)
        .then((response) => {
          console.log("profile update", response);
          this.$router.push("/profile");
        })
        .catch((error) => {
          console.log("profile update error", error.response);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="profile">
    <h2>{{ "Look at your beautiful profile!" }}</h2>
    <img :src="profile.photo_url" class="w3-round" />
    <p>Name: {{ profile.first_name + " " + profile.last_name }}</p>
    <p>Email: {{ profile.email }}</p>
    <p>Phone Number: {{ profile.phone_number }}</p>
    <p>Bio: {{ profile.short_bio }}</p>
    <p>Linkedin: {{ profile.linkedin_url }}</p>
    <p>Resume: {{ profile.resume_url }}</p>
    <p>Personal Blog: {{ profile.personal_blog_url }}</p>
    <p>Github: {{ profile.github_url }}</p>
    <p>Twitter: {{ profile.twitter_handle }}</p>

    <form method="dialog">
      <h1>profile info</h1>
      <p>
        first Name:
        <input type="text" v-model="editProfileParams.first_name" />
      </p>
      <p>
        Last Name:
        <input type="text" v-model="editProfileParams.last_name" />
      </p>
      <p>
        Email:
        <input type="text" v-model="editProfileParams.email" />
      </p>
      <p>
        PhoneNumber:
        <input type="text" v-model="editProfileParams.phone_number" />
      </p>
      <p>
        Bio:
        <input type="text" v-model="editProfileParams.short_bio" />
      </p>
      <p>
        Linkedin:
        <input type="text" v-model="editProfileParams.linkedin_url" />
      </p>
      <p>
        Twitter:
        <input type="text" v-model="editProfileParams.twitter_handle" />
      </p>
      <p>
        Portfolio:
        <input type="text" v-model="editProfileParams.personal_blog_url" />
      </p>
      <p>
        Resume:
        <input type="text" v-model="editProfileParams.resume_url" />
      </p>
      <p>
        Github:
        <input type="text" v-model="editProfileParams.github_url" />
      </p>
      <p>
        Picture:
        <input type="text" v-model="editProfileParams.photo_url" />
      </p>
      <button v-on:click="updateProfile(currentProfile)">Update</button>
      <button>Close</button>
    </form>
  </div>
</template>
