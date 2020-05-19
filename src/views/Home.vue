<template>
  <div class="home">
    <h1>All Contests</h1>
      <div v-for="forecast in forecasts">
        <h2>{{ forecast.dateTimeISO }}</h2>
        <p>Over/Under: {{ forecast.maxTempF }} Farenheit</p>
        <p>Moneyline: -110</p>
        <p>City: Chicago</p>
        <router-link to="/bets/new">Bet</router-link>
      </div>
    </div>
  </div>
</template>
<style></style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      forecasts: [],
      contests: [],
    };
  },
  created: function() {
    axios.get("/api/forecasts").then(response => {
      this.forecasts = response.data;
    });
    axios.get("/api/contests").then(response => {
      this.contests = response.data;
    });
  },
  methods: {
    onPressLearnMore: function() {
      alert("Hello");
    },
  },
};
</script>
