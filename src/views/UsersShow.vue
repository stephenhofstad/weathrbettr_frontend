<template>
  <div class="UsersShow">
    <h3>Profile</h3>
    <table id="userTable">
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Balance</th>
        </tr>
      </thead>
      <tbody>
          <td>{{user.name}}</td>
          <td>{{user.email}}</td>
          <td>${{user.balance}}.00</td>
        </tr>
      </tbody>
    </table>
    <h3>Bet History</h3>
    <table id="firstTable">
      <thead>
        <tr>
          <th>Date</th>
          <th>Game</th>
          <th>Line</th>
          <th>Amount</th>
          <th>Pick</th>
          <th>Temperature</th>
          <th></th>
          <th>Status</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="bet in user.bets">
          <td>{{bet.contest.date}}</td>
          <td>{{bet.contest.game}}</td>
          <td>{{bet.contest.line}} °F</td>
          <td>${{bet.amount}}.00</td>
          <td>{{bet.pick}}</td>
          <td>{{bet.contest.real_temp}} °F</td>
          <td> <button v-on:click="updateTemp(bet.contest)">Show Temp</button> </td>
          <td>{{bet.status}}</td>
  
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<style>
table {
  font-family: "Open Sans", sans-serif;
  width: 750px;
  border-collapse: collapse;
  border: 3px solid #44475c;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475c;
  color: #fff;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7d82a8;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #d4d8f9;
}


</style>
<script>
var axios = require("axios");

export default {
  data: function() {
    return {
      real_temp: "",
      user: {},
      tempers: [],

    };
  },
  created: function() {
    axios.get("/api/users/profile").then(response => {
      console.log(response);
      this.user = response.data;
    });
    axios.get("/api/tempers").then(response => {
      this.tempers = response.data;
    });
  },
  
  methods: {
    updateTemp: function(contest) {
      var params = {
        real_temp: this.tempers[0][0][1],
        
      };
      axios
        .patch("/api/contests/" + contest.id, params)
        .then(response => {
          // this.$router.push("/users/profile");
          console.log(response)
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    },
  },                                            
};
</script>