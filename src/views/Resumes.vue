<script>
import axios from "axios";
export default {
  data: function () {
    return {
      resumes: [],
      experience: [
        {
          startDate: "",
          endDate: "",
          jobTitle: "",
          companyName: "",
          details: "",
        },
      ],
      education: [
        {
          startDate: "",
          endDate: "",
          degree: "",
          universityName: "",
          details: "",
        },
      ],
      skills: [
        {
          skillName: "",
        },
      ],
      projects: [
        {
          name: "",
          description: "",
          url: "",
          screenshot: "",
        },
      ],
    };
  },
  created: function () {
    this.getStudents();
  },
  methods: {
    getStudents: function () {
      axios.get("https://fierce-cove-12825.herokuapp.com/students").then((response) => {
        console.log(response.data);
        this.resumes = response.data;
      });
    },
  },
};
</script>

<template>
  <div v-for="resume in resumes" :key="resume.id">
    <h1>Profile</h1>
    <p>First Name: {{ resume.first_name }}</p>
    <p>Second Name: {{ resume.last_name }}</p>
    <p>Email: {{ resume.email }}</p>
    <p>Phone Number: {{ resume.phone_number }}</p>
    <p>Bio: {{ resume.short_bio }}</p>
    <p><a href="resume.linkedin_url">LinkdIN</a></p>
    <p>Twitter: {{ resume.twitter_handle }}</p>
    <p><a href="resume.personal_blog_url">Personal Blog</a></p>
    <p><a href="resume.resume_url"></a></p>
    <p><a href="resume.github_url">GitHub</a></p>
    <img src="resume.photo_url" alt="personal image" />
    <h1>Experience</h1>
    <h1>Education</h1>
    <h1>Skills</h1>
    <h1>Projects</h1>
    <p>__________________________</p>
  </div>
</template>
