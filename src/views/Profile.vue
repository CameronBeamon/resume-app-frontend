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
    console.log("looks like it's working");
  },
  methods: {
    updateProfile: function (profile) {
      axios
        .patch("/students/" + profile.id, this.editProfileParams)
        .then((response) => {
          console.log("profile update", response);
          this.$router.push("/");
        })
        .catch((error) => {
          console.log("products update error", error.response);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>

<template>
  <div class="profile">
    <h2>{{ "This is going to look great trust me" }}</h2>
    <p>{{ "Like I said, It'll look great" }}</p>
    <dialog id="photo-details">
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
    </dialog>
  </div>
</template>
