<template>
  <div class="home">
    <div class="info">
      <p>Do you want to join our amazing agency? Want to grow your skills? <br> Click <span>Below</span> </p>
      <router-link to="/register"><button>Apply </button></router-link>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
};
</script>
<style scoped>
* {
  box-sizing: border-box;
}

.home {
  background-image: url(../assets/homebg.jpg);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 100vh;
  width: 100%;
  background-blend-mode: overlay;
  background-color: rgb(24, 24, 24);
  padding: 1px;
  margin-top: 1px;
  overflow: hidden;
}

.home .info {
  text-align: center;
  margin: 250px ;
}

.info p {
  /* margin-top: 150px; */
  color: #fff;
  font-size: 20px;
}

.info p span {
  color: aqua;
}

.info button {
  background: #000;
  color: #eeffff;
  width: 150px;
  padding: 10px;
  border: 1px solid #eee;
  transition: linear 0.2s;
}

.info button:hover {
  background: transparent;
}

.info a:hover {
  background: none;
  text-decoration: none;
}



</style>