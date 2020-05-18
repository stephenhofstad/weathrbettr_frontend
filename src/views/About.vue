<template>
  <div class="home">
    <h1>Temperature Past 24 Hours</h1>
    <div v-for="temper in tempers">
      <h2>{{ temper }}</h2>
      <!-- <p>Over/Under: {{ temper.maxTempF }} Farenheit</p>
      <p>Moneyline: -110</p>
      <p>City: Chicago</p>-->
    </div>
  </div>
</template>
<style></style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      tempers: [],
    };
  },
  created: function() {
    axios.get("/api/tempers").then(response => {
      this.tempers = response.data;
    });
  },
  methods: {},
};
</script>