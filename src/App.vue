<template>
  <div id="wrapper">
    <div id="nav">
      <router-link to="/">All Contests</router-link>
      |
      <router-link to="/users/profile">User Info</router-link>
      |
      <router-link to="/SignUp">Signup</router-link>
      |
      <router-link to="/Login">Login</router-link>
      |
      <router-link to="/Logout">Logout</router-link>
      |
      <router-link to="/About">24 Hour History</router-link>
      |
      <router-link to="/bets/new">Place a Bet</router-link>
      <head>
        <title>Phantom by HTML5 UP</title>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
        <link rel="stylesheet" href="/assets/css/main.css" />
        <a href="/about">About Us</a>
        <noscript>
          <link rel="stylesheet" href="/assets/css/noscript.css" />
        </noscript>
      </head>
    </div>
    <div id="main">
      <div class="inner">
        <router-view />
      </div>
    </div>
    <footer id="footer">
      <div class="inner">
        <section>
          <h2>Have a gambling problem? Get in touch!</h2>
          <form method="post" action="#">
            <div class="fields">
              <div class="field half">
                <input type="text" name="name" id="name" placeholder="Name" />
              </div>
              <div class="field half">
                <input type="email" name="email" id="email" placeholder="Email" />
              </div>
              <div class="field">
                <textarea name="message" id="message" placeholder="Tell us your favorite game!"></textarea>
              </div>
            </div>
            <ul class="actions">
              <li>
                <input type="submit" value="Send" class="primary" />
              </li>
            </ul>
          </form>
        </section>
        <section>
          <h2>Follow</h2>
          <ul class="icons">
            <li>
              <a href="#" class="icon brands style2 fa-twitter">
                <span class="label">Twitter</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon brands style2 fa-facebook-f">
                <span class="label">Facebook</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon brands style2 fa-instagram">
                <span class="label">Instagram</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon brands style2 fa-dribbble">
                <span class="label">Dribbble</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon brands style2 fa-github">
                <span class="label">GitHub</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon brands style2 fa-500px">
                <span class="label">500px</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon solid style2 fa-phone">
                <span class="label">Phone</span>
              </a>
            </li>
            <li>
              <a href="#" class="icon solid style2 fa-envelope">
                <span class="label">Email</span>
              </a>
            </li>
          </ul>
        </section>
        <ul class="copyright">
          <li>&copy; Untitled. All rights reserved</li>
          <li>
            Design:
            <a href="http://html5up.net">HTML5 UP</a>
          </li>
        </ul>
      </div>
    </footer>
  </div>
</template>

<style>
body {
  background-image: url("./assets/weather.png");
}
</style>

<script>
export default {
  data: function() {
    return {
      jwt: null,
      userId: null,
    };
  },
  created: function() {
    this.setJwt();
    this.setUserId();
  },
  methods: {
    setJwt: function() {
      this.jwt = localStorage.jwt;
    },
    setUserId: function() {
      this.userId = parseInt(localStorage.user_id);
    },
  },
};
</script>
