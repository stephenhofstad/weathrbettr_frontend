<template>
  <div class="bets-new">
    <br></br>
    <form v-on:submit.prevent="newBet()">
      <label for="contest_id">Contest Date:</label>
    
      <!-- <input type="text" v-model="contest_id" id="contest_id" name="contest_id" /> -->
     <select v-model="contest_id">
       <option value="5">5/23/20</option>
       <option value="6">5/24/20</option>
       <option value="7">5/25/20</option>
       <option value="8">5/26/20</option>
       <option value="9">5/27/20</option>
       <option value="10">5/28/20</option>
     </select>
      <label for="amount">Amount:</label>
      
      <input type="text" v-model="amount" id="amount" name="amount" />
      <br />
      <label for="pick">Pick:</label>
      <input type="radio" v-model="pick" id="under" name="pick" value="under" />
      <label for="under">Under</label>
      <br />
      <input type="radio" v-model="pick" id="over" name="pick" value="over" />
      <label for="over">Over</label>
      <br />
      <input type="submit" class="btn btn-primary" value="Submit" />
    </form>
  </div>
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