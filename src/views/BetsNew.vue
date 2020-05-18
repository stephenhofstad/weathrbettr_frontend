<template>
  <div class="container">
    <form v-on:submit.prevent="createBet()">
      <h1>New Bet</h1>
      <ul>
        <li class="text-danger" v-for="error in errors">{{ error }}</li>
      </ul>
      <label>Amount:</label>
      <input type="text" v-model="newBetAmount" />
      Pick:
      <input type="text" v-model="newBetPick" />
      Contest Id:
      <input type="text" v-model="newContestId" />
      <input type="submit" value="Create" />
    </form>
  </div>
</template>


<script>
import axios from "axios";

export default {
  data: function() {
    return {
      newBetAmount: "",
      newBetPick: "",
      newContestId: "",
      errors: [],
    };
  },
  created: function() {},
  methods: {
    createBet: function() {
      var params = {
        amount: this.newBetAmount,
        pick: this.newBetPick,
        contest_id: this.newContestId,
      };
      axios
        .post("/api/bets", params)
        .then(response => {
          this.$router.push("/users/profile");
        })
        .catch(error => {
          console.log(error.response);
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>