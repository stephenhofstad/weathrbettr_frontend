 <template>
  <div class="home">
    <h1>All Contests</h1>
    <div v-for="contest in contests">
      <h2>{{ contest.date }}</h2>
      <p>Cutoff: {{ contest.time }}</p>
      <p>Win: {{ contest.win }}</p>
      <p>Temp: {{ contest.line }}</p>
    </div>
  </div>
</template>
 <style>
</style>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      contests: [],
    };
  },
  created: function() {
    axios.get("/api/contests").then(response => {
      this.contests = response.data;
    });
  },
  methods: {},
};
</script>