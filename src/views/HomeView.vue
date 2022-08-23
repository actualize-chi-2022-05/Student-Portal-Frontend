<script>
import axios from "axios";
export default {
  data: function () {
    return {
      educations: [],
    };
  },
  created: function () {
    this.indexEducations();
  },
  methods: {
    indexEducations: function () {
      axios.get("/educations").then((response) => {
        console.log("educations index", response);
        this.educations = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="home">
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
