<script>
import axios from "axios";
export default {
  data: function () {
    return {
      resumes: [],
      experience: [],
      education: [],
      skills: [],
      projects: [],
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
        this.experience = this.resumes.experiences;
        this.education = this.resumes.educations;
        this.projects = this.resumes.projects;
        this.skills = this.resumes.skills;
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
    <img v-bind:src="resume.photo_url" alt="personal image" class="profile-photo" />
    <h1>Experience</h1>
    <p>{{ experiences }}</p>
    <h1>Education</h1>
    <p>{{ educations }}</p>
    <h1>Skills</h1>
    <p>{{ resume.skills }}</p>
    <h1>Projects</h1>
    <p>{{ resume.projects }}</p>
    <p>__________________________</p>
  </div>
</template>

<style>
.profile-photo {
  width: 50px;
}
</style>
