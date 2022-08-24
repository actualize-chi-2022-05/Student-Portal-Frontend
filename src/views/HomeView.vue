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
    this.indexExperience();
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
        this.experience = response.data;
      });
    },
    indexSkills: function () {
      axios.get("/skills").then((response) => {
        console.log("skills index", response);
        this.experience = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>

  <div class="skill">
    <h1>Experience</h1>
    <div v-for="skill in skills" v-bind:key="skill.id">
      <p>Skill: {{ skill.name }}</p>
    </div>
  </div>
  <div class="experience">
    <h1>Experience</h1>
    <div v-for="experience in experiences" v-bind:key="experience.id">
      <p>Start Date: {{ experience.startDate }}</p>
      <p>End Date: {{ experience.endDate }}</p>
      <p>Job Title: {{ experience.jobTitle }}</p>
      <p>Company Name: {{ experience.companyName }}</p>
      <p>Details: {{ experience.details }}</p>
    </div>
  </div>
  <div class="capstone">
    <div class="container">
      <h1>Capstone Name: {{ capstone.name }}</h1>
      <div v-for="capstone in capstones" v-bind:key="capstone.id">
        <p>Description: {{ capstone.description }}</p>
        <p>Capstone URL: {{ capstone.url }}</p>
        <img src="screenshot" alt="capstone-screenshot" />
      </div>
    </div>
  </div>
  <div class="education">
    <h1>Education</h1>
    <div v-for="education in educations" v-bind:key="education.id">
      <h2>{{ education.name }}</h2>
      <img v-bind:src="photo.url" v-bind:alt="photo.name" />
      <p>Start Date: {{ education.startDate }}</p>
      <p>End Date: {{ education.endDate }}</p>
      <p>Degree: {{ education.degree }}</p>
      <p>Details: {{ education.details }}</p>
    </div>
  </div>
</template>

<style></style>
