<script>
export default {
  data: function () {
    return {
      isLoggedIn: false,
      flashMessage: "",
    };
  },
  methods: {
    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
  watch: {
    $route: function () {
      this.isLoggedIn = !!localStorage.jwt;
      this.flashMessage = localStorage.getItem("flashMessage");
      this.flashMessage = localStorage.removeItem("flashMessage");
    },
  },
};
</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Student Portal</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li><a class="nav-link" href="/home">Student Data</a></li>
          <li><a v-if="!isLoggedIn" class="nav-link" href="/login">Sign In</a></li>
          <li><a v-if="isLoggedIn" class="nav-link" href="/logout">Sign Out</a></li>
        </ul>
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
          <button class="btn btn-success" type="submit">Search</button>
        </form>
      </div>
    </div>
  </nav>

  <div v-if="this.flashMessage" class="alert alert-success">
    {{ flashMessage }}
  </div>
  <router-view />
</template>

<style>
#app {
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
