<template>
  <div id="nav" class="nav-bar">
    
    <router-link to="/" style="float: left;" class="logo">Logo</router-link> 
    <!-- <router-link to="/">Home</router-link> 
    <router-link to="/posts">Posts</router-link>  -->
    <span v-if="isLoggedIn">
      <a @click="logout">Logout</a>
    </span>
    <span v-else>
      <router-link to="/register">Register</router-link> 
      <router-link to="/login">Login</router-link>
    </span>
  </div>
</template>


<script>
  export default {
    name: "NavBar",
    computed: {
      isLoggedIn: function() {
        return this.$store.getters.isAuthenticated;
      },
    },
    methods: {
      async logout() {
        await this.$store.dispatch("LogOut");
        this.$router.push("/login");
      },
    },
  };
</script>

<style>
  .nav-bar {
    background-color: #000;
    color: #fff;
    padding: 30px;
    overflow: hidden;
    /* margin: -8px */
  }

  .nav-bar .logo {
    float: left;
    color: #fff;
    font-size: 25px;
    text-decoration: none;
    text-transform: uppercase;
    text-shadow: -4px -2px 0px #bdbdbd;
  }
  .nav-bar a {
    font-weight: bold;
    color: #bebebe;
    margin-right: 30px;
    text-align: right;
    text-decoration: none;
    transition: all linear 0.3s;
    float: right;
  }

  a:hover {
    cursor: pointer;
    color: rgb(226, 226, 226);
    background: #333;
    padding: 2px;
  }

  #nav a.router-link-exact-active {
    color: #ffffff;
  }
</style>
