<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

import { assertExpressionStatement } from "@babel/types";

export default {
  data: function () {
    return {
      experience: [],
    };
  },
  created: function () {
    this.indexExperience();
  },
  methods: {
    indexExperience: function () {
      axios.get("/experience").then((response) => {
        console.log("experience index", response);
        this.experience = response.data;
      });
    },
  },
};
</script>

<template>
  <div class="experience">
    <h1>Experience</h1>
    <div v-for="experience in experience" v-bind:key="experience.id">
      <p>Start Date: {{ experience.startDate }}</p>
      <p>End Date: {{ experience.endDate }}</p>
      <p>Job Title: {{ experience.jobTitle }}</p>
      <p>Company Name: {{ experience.companyName }}</p>
      <p>Details: {{ experience.details }}</p>
    </div>
  </div>
</template>
