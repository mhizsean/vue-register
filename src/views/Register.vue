<template>
  <div class="register">
    <div>
      <form @submit.prevent="submit">
        <div>
          <label for="email">email </label> <br>
          <input type="text" name="email" v-model="form.email" />
        </div>
        <div>
          <label for="username">Username</label> <br>
          <input type="text" name="username" v-model="form.username" />
        </div>
        <div>
          <label for="full_name">Full Name</label> <br>
          <input type="text" name="full_name" v-model="form.full_name" />
        </div>
        <div>
          <label for="password">Password</label> <br>
          <input type="password" name="password" v-model="form.password" />
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
    <p v-if="showError" id="error">Username already exists</p>
  </div>
</template>

<script>
  import { mapActions } from "vuex";

  export default {
    name: "Register",
    components: {},
    data() {
      return {
        form: {
          email: "",
          username: "",
          full_name: "",
          password: "",
        },
        showError: false
      };
    },
    methods: {
      ...mapActions(["Register"]),
      async submit() {
        try {
          await this.Register(this.form);
          this.$router.push("/homelogin");
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

.register {
    width: 30%;
  margin: 70px auto;
  padding: 60px ;
  background-color: #eee;
  box-shadow: -1px 1px 10px ;
}
label {
  padding: 12px 12px 12px 0;
  display: inline-block;
  text-align: left;
  text-transform: capitalize;
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
  background-color: #3a3a3a;
}

input {
  margin: 5px;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.06);
  padding: 10px;
  border-radius: 5px;
  width: 100%;
}
#error {
  color: red;
}
</style>
