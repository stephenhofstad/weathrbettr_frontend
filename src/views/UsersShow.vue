<template>
  <div class="UsersShow">
    <div v-for="user in users">
      <h2>{{ user.first_name }}</h2>
      <h2>{{ user.last_name }}</h2>
    </div>
  </div>
</template>

<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      users: {},
    };
  },
  created: function() {
    axios.get("/api/users/" + this.$route.params.id).then(response => {
      this.users = response.data;
    });
  },
  methods: {},
};
</script>