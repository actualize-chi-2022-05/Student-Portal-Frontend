<script>
export default {
  data: function () {
    return {
      isLoggedIn: false,
      // flashMessage: "",
      darkMode: false,
    };
  },
  methods: {
    getUserId: function () {
      return localStorage.getItem("user_id");
    },
  },
  watch: {
    $route: function () {
      // this.isLoggedIn = !!localStorage.jwt;
      // this.flashMessage = localStorage.getItem("flashMessage");
      // this.flashMessage = localStorage.removeItem("flashMessage");
    },
  },
  dark() {
    document.querySelector("body").classList.add("dark-mode");
    this.darkMode = true;
    this.$emit("dark");
  },

  light() {
    document.querySelector("body").classList.remove("dark-mode");
    this.darkMode = false;
    this.$emit("light");
  },

  modeToggle() {
    if (this.darkMode || document.querySelector("body").classList.contains("dark-mode")) {
      this.light();
    } else {
      this.dark();
    }
  },

  computed: {
    darkDark() {
      return this.darkMode && "darkmode-toggled";
    },
  },
};
</script>

<template>
  <nav class="navbar sticky-top navbar-expand-lg navbar-dark" style="background-color: #19a6c8">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">
        <img src="./assets/studentPortal.png" alt="" width="50" height="50" class="d-inline-block align-text-top" />
        Student Portal
      </a>
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
          <li>
            <a class="nav-link" href="/">Student Data</a>
          </li>
          <li>
            <a v-if="!isLoggedIn" class="nav-link" href="/login">Sign In</a>
          </li>
          <li>
            <a v-if="isLoggedIn" class="nav-link" href="/logout">Sign Out</a>
          </li>
        </ul>
        <form class="d-flex" role="search">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" />
          <button
            class="btn btn-outline-dark"
            style="--bs-btn-padding-y: 0.25rem; --bs-btn-padding-x: 0.5rem; --bs-btn-font-size: 1rem"
            type="submit"
          >
            Search
          </button>
          <div>
            <!-- Rounded switch -->
            <label class="switch">
              <input type="checkbox" onchange="darkMode()" />
              <span class="slider round"></span>
              <!-- <toggle onclick="darkMode()">Darkmode</toggle> -->
            </label>
          </div>
        </form>
      </div>
    </div>
  </nav>
  <!-- <div v-if="this.flashMessage" class="alert alert-success">
    {{ flashMessage }}
  </div> -->
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
