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
      });
    },
  },
};
</script>
