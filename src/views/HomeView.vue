<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

import { assertExpressionStatement } from "@babel/types";

export default {
  data: function () {
    return {
      experiences: [],
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
=======
<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
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
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";
export default {
  data: function () {
    return {
      capstones: [],
    };
  },
  created: function () {
    this.indexCapstones();
  },
  methods: {
    indexCapstone: function () {
      axios.get("/capstones").then((response) => {
        console.log("capstones index", response);
        this.capstones = response.data;
>>>>>>> ef3785c83935fb9b0082f13914971831378b00b1
      });
    },
  },
};
</script>

<template>
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
</template>
