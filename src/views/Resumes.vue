<script>
import axios from "axios";
export default {
  data: function () {
    return {
      resumes: [],
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
    <img v-bind:src="resume.photo_url" alt="personal image" class="profile-photo" />
    <h1>Experience</h1>
    <div v-for="experience in resume.experiences" :key="experience.id">
      <p>{{ experience.company_name }}</p>
    </div>
    <h1>Education</h1>
    <div v-for="education in resume.educations" :key="education.id">
      <p>{{ education.university_name }}</p>
      <p>{{ education.degree }}</p>
      <p>{{ education.details }}</p>
      <p>{{ education.start_date }}</p>
      <p>{{ education.end_date }}</p>
    </div>
    <h1>Skills</h1>
    <div v-for="skill in resume.skills" :key="skill.id">
      <p>{{ skill.skill_name }}</p>
    </div>
    <h1>Projects</h1>
    <div v-for="project in resume.projects" :key="project.id">
      <p>{{ project.project_name }}</p>
      <p>{{ project.description }}</p>
      <img :src="project.project_screenshot" alt="" class="project-photo" />
      <a href="project.project_url">Project Link</a>
    </div>
    <p>__________________________</p>
  </div>
</template>

<style>
.profile-photo {
  width: 50px;
}
.project-photo {
  width: 50px;
}
</style>
