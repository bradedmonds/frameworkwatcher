<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <apexchart align = "center" width="1000" type="bar" :options="options" :series="series"></apexchart>
  </div>

</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to my frontend framework tracker!",
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
      options: {
        chart: {
          id: "vuechart-example",
        },
        xaxis: {
          categories: ["Forks", "Watchers", "Stars"],
        },
      },
      series: [
        {
          name: "Vue",
          data: [],
        },
        {
          name: "Angular",
          data: [],
        },
        {
          name: "Ember",
          data: [],
        },
        {
          name: "Svelte",
          data: [],
        },
        {
          name: "React",
          data: [],
        },
      ],
    };
  },
  created: function () {
    axios.get("https://api.github.com/repos/vuejs/vue").then((response) => {
      console.log(response.data);
      this.vueForks = response.data.forks;
      this.vueWatchers = response.data.watchers;
      this.vueStars = response.data.stargazers_count;
      this.series = [{ data: [this.vueForks, this.vueStars, this.vueStars] }];
    });
    axios.get("https://api.github.com/repos/angular/angular.js").then((response) => {
      console.log(response.data);
      this.angularForks = response.data.forks;
      this.angularWatchers = response.data.watchers;
      this.angularStars = response.data.stargazers_count;
      this.series = [{}, { name: "Angular", data: [this.angularForks, this.angularStars, this.angularStars] }];
    });
    axios.get("https://api.github.com/repos/emberjs/ember.js").then((response) => {
      console.log(response.data);
      this.emberForks = response.data.forks;
      this.emberWatchers = response.data.watchers;
      this.emberStars = response.data.stargazers_count;
      this.series = [{}, {}, { name: "Ember", data: [this.emberForks, this.emberStars, this.emberStars] }];
    });
    axios.get("https://api.github.com/repos/sveltejs/svelte").then((response) => {
      console.log(response.data);
      this.svelteForks = response.data.forks;
      this.svelteWatchers = response.data.watchers;
      this.svelteStars = response.data.stargazers_count;
      this.series = [{}, {}, {}, { name: "Svelte", data: [this.svelteForks, this.svelteStars, this.svelteStars] }];
    });
    axios.get("https://api.github.com/repos/facebook/react").then((response) => {
      console.log(response.data);
      this.reactForks = response.data.forks;
      this.reactWatchers = response.data.watchers;
      this.reactStars = response.data.stargazers_count;
      this.series = [{}, {}, {}, {}, { name: "React", data: [this.reactForks, this.reactStars, this.reactStars] }];
    });
  },
  methods: {},
};
</script>

