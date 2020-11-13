<template>
  <div class="login">
    <div>
      <form @submit.prevent="submit">
        <div>
          <input type="text" name="username" placeholder="Enter username" v-model="form.username" />
        </div>
        <div>
          <input type="password" name="password" placeholder="*****************" v-model="form.password" />
        </div>
        <button type="submit">Submit</button>
      </form>
      <p v-if="showError" id="error">Please fill in valid login details</p>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  name: "Login",
  components: {},
  data() {
    return {
      form: {
        username: "",
        password: "",
      },
      showError: false
    };
  },
  methods: {
    ...mapActions(["LogIn"]),
    async submit() {
      const User = new FormData();
      User.append("username", this.form.username);
      User.append("password", this.form.password);
      try {
          await this.LogIn(User);
          this.$router.push("/posts");
          this.showError = false
      } catch (error) {
        this.showError = true
      }
    },
  },
};
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.login {
  width: 30%;
  margin: 70px auto;
  padding: 60px ;
  background-color: #eee;
  box-shadow: -1px 1px 10px ;
}

label {
  padding: 12px 12px 12px 0;
  display: inline-block;
}

button[type="submit"] {
  background-color: #5b695b;
  color: white;
  padding: 12px 20px;
  cursor: pointer;
  border: none;
  border-radius: 10px;
  margin-top: 10px;
  width: 100%;
  transition: all linear 0.3s;
  text-transform: uppercase;
}

button[type="submit"]:hover {
  background-color: #aaaaaa;
  color: #393a39; 

}

input {
  width: 100%;
  margin: 5px;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.06);
  padding: 10px;
  border: none;
  outline: none;
  border-radius: 50px;
}

#error {
  color: red;
}
</style>
