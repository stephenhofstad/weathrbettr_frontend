<template>
  <div class="home">
    <h1>Temperature Past 24 Hours</h1>
    <div v-for="temper in tempers">
      <h4>Time:{{ temper[0][0] }}</h4>
      <h4>Temperature Farenheit:{{ temper[0][1] }}</h4>
      <br />
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