<script>
export default {
  data: function () {
    return {
      profile: {
        id: 1,
        FirstName: "Kurt",
        LastName: "Proepper",
        Email: "",
        PhoneNumber: "",
        ShortBio: "",
        LinkedInURL: "",
        TwitterHandle: "@KProepper",
        PersonalBlogWebsite: "",
        OnlineResume: "",
        GithubURL: "",
        Photo:
          "https://media-exp1.licdn.com/dms/image/C4D03AQGtmJvoRL22AQ/profile-displayphoto-shrink_200_200/0/1644709838180?e=1650499200&v=beta&t=K3A9PhYXsy3_0JJGoLIit_ZbRdhzxfO81S3xuDcSVzM",
      },
    };
  },
  created: function () {
    console.log("looks like it's working");
  },
  methods: {},
};
</script>

<template>
  <div class="profile">
    <img v-bind:src="profile.Photo" v-bind:alt="profile.FirstName" />
    <h2>{{ profile.FirstName }}</h2>
    <p>{{ profile }}</p>
  </div>
</template>
