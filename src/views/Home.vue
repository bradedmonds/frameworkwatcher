<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style>
</style>

<script>
const axios = require("axios");
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then(function (response) {
      console.log(response.data);
      console.log(response.data.forks);
      console.log(response.data.watchers);
      console.log(response.data.stargazers_count);
    });
  },
  methods: {},
};
</script>

