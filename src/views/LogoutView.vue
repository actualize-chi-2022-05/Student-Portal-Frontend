<script>
import axios from "axios";

export default {
  created: function () {
    delete axios.defaults.headers.common["Authorization"];
    localStorage.removeItem("jwt");
    localStorage.setItem(("flashMessage", "User Logged Out"));
    this.$router.push("/posts");
  },
};
</script>

<template>
  <div class="logout"></div>
</template>
