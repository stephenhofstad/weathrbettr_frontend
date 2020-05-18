<template>
  <form v-on:submit.prevent="newBet()">
    <label for="contest_id">contest_id:</label>
    <br />
    <input type="text" id="contest_id" name="contest_id" />
    <br />
    <label for="amount">Amount:</label>
    <br />
    <input type="text" id="amount" name="amount" />
    <br />
    <label for="pick">Pick:</label>
    <input type="radio" id="under" name="pick" value="under" />
    <label for="under">Under</label>
    <br />
    <input type="radio" id="over" name="pick" value="over" />
    <label for="over">Over</label>
    <br />
    <input type="submit" class="btn btn-primary" value="Submit" />
  </form>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      contest_id: "",
      amount: "",
      pick: "",
      errors: [],
    };
  },
  methods: {
    newBet: function() {
      var params = {
        contest_id: this.contest_id,
        amount: this.amount,
        pick: this.pick,
      };
      axios
        .post("/api/bets", params)
        .then(response => {
          this.$router.push("/users/profile");
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    },
  },
};
</script>