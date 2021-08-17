<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>Fork Count: {{ vueForks }}</h2>
    <h2>Watchers: {{ vueWatchers }}</h2>
    <h2>Stars: {{ vueStars }}</h2>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      vueForks: 0,
      vueWatchers: 0,
      vueStars: 0,
      angularForks: 0,
      angularWatchers: 0,
      angularStars: 0,
      emberForks: 0,
      emberWatchers: 0,
      emberStars: 0,
      svelteForks: 0,
      svelteWatchers: 0,
      svelteStars: 0,
      reactForks: 0,
      reactWatchers: 0,
      reactStars: 0,
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
      console.log(response.data);
      this.vueForks = response.data.forks;
      this.vueWatchers = response.data.watchers;
      this.vueStars = response.data.stargazers_count;
    });
    axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
      console.log(response.data);
      this.angularForks = response.data.forks;
      this.angularWatchers = response.data.watchers;
      this.angularStars = response.data.stargazers_count;
    });
    axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
      console.log(response.data);
      this.emberForks = response.data.forks;
      this.emberWatchers = response.data.watchers;
      this.emberStars = response.data.stargazers_count;
    });
    axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
      console.log(response.data);
      this.svelteForks = response.data.forks;
      this.svelteWatchers = response.data.watchers;
      this.svelteStars = response.data.stargazers_count;
    });
    axios.get("https://api.github.com/repos/facebook/react").then((response) => {
      console.log(response.data);
      this.reactForks = response.data.forks;
      this.reactWatchers = response.data.watchers;
      this.reactStars = response.data.stargazers_count;
    });
  },
  methods: {},
};
</script>

