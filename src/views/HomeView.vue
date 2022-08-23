<template>
  <div class="experience">
    <h1>Experience</h1>
    <div v-for="experience in experience" v-bind:key="experience.id" >
    <p>Start Date: {{ experience.startDate }}</p>
    <p>End Date: {{ experience.endDate }}</p>
    <p>Job Title: {{ experience.jobTitle }}</p>
    <p>Company Name: {{ experience.companyName }}</p>
    <p>Details: {{ experience.details }}</p>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
};
</script>
