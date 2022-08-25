<script>
import axios from "axios";
export default {
  data: function () {
    return {
      educations: [],
      experiences: [],
      capstones: [],
      skills: [],
    };
  },
  created: function () {
    this.indexEducations();
    this.indexExperiences();
    this.indexCapstones();
    this.indexSkills();
  },
  methods: {
    indexEducations: function () {
      axios.get("/educations").then((response) => {
        console.log("educations index", response);
        this.educations = response.data;
      });
    },
    indexCapstones: function () {
      axios.get("/capstones").then((response) => {
        console.log("capstones index", response);
        this.capstones = response.data;
      });
    },
    indexExperiences: function () {
      axios.get("/experiences").then((response) => {
        console.log("experiences index", response);
        this.experiences = response.data;
      });
    },
    indexSkills: function () {
      axios.get("/skills").then((response) => {
        console.log("skills index", response);
        this.skills = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <h1>Welcome Students to your resume data</h1>
  </div>
  <div class="skill">
    <h3>Skill</h3>
    <div v-for="skill in skills" v-bind:key="skill.id">
      <p>Skill: {{ skill.skill }}</p>
    </div>
  </div>
  <div class="experience">
    <h3>Experience</h3>
    <div v-for="experience in experiences" v-bind:key="experience.id">
      <p>Job Title: {{ experience.job_title }}</p>
      <p>Company Name: {{ experience.company_name }}</p>
      <p>Start Date: {{ experience.start_date }}</p>
      <p>End Date: {{ experience.end_date }}</p>
      <p>Details: {{ experience.details }}</p>
    </div>
  </div>
  <div class="capstone">
    <!-- <h3>Capstone</h3> -->
    <div v-for="capstone in capstones" v-bind:key="capstone.id">
      <h3>Capstone Name: {{ capstone.name }}</h3>
      <p>Description: {{ capstone.description }}</p>
      <p>Capstone URL: {{ capstone.url }}</p>
      <img v-bind:src="capstone.screenshot" alt="capstone screenshot" height="200  " />
    </div>
  </div>
  <div class="education">
    <h3>Education</h3>
    <div v-for="education in educations" v-bind:key="education.id">
      <h2>{{ education.name }}</h2>
      <h5>University: {{ education.university_name }}</h5>
      <p>Start Date: {{ education.start_date }}</p>
      <p>End Date: {{ education.end_date }}</p>
      <p>Degree: {{ education.degree }}</p>
      <p>Details: {{ education.details }}</p>
    </div>
  </div>
</template>

<style></style>
