<script>
export default {
  data: function () {
    return {
      resumes: [
        {
          id: 1,
          FirstName: "Testname",
          LastName: "",
          Email: "",
          PhoneNumber: "",
          ShortBio: "",
          LinkedInURL: "",
          TwitterHandle: "",
          PersonalBlogWebsite: "",
          OnlineResume: "",
          GithubURL: "",
          Photo: "",
        },
      ],
    };
  },
  created: function () {},
  methods: {},
};
</script>

<template>
  <div v-for="resume in resumes" :key="resume.id">
    <p>{{ resume.FirstName }}</p>
    <p>{{ resume.LastName }}</p>
    <p>{{ resume.Email }}</p>
    <p>{{ resume.PhoneNumber }}</p>
    <p>{{ resume.ShortBio }}</p>
    <p>{{ resume.LinkedInURL }}</p>
    <p>{{ resume.TwitterHandle }}</p>
    <p>{{ resume.PersonalBlogWebsite }}</p>
    <p>{{ resume.OnlineResume }}</p>
    <p>{{ resume.GithubURL }}</p>
    <p>{{ resume.Photo }}</p>
  </div>
</template>
