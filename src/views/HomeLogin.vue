<template>
  <div class="container">
    <div v-if="User" class="user-hi">
      <h2>Howdy <span>{{ User }}</span>!</h2>
    </div>
    <div>
      <div class="next">
          <p>We hope the infomation you entered is accurate, as your fullname - {{ fullname }}</p>
      </div>
      

    </div>
  
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  name: "HomeLogin",
  components: {},
  data() {
    return {
      form: {
        title: "",
        write_up: "",
      },
    };
  },

  computed: {
    ...mapGetters({ User: "StateUser" }),
  },
  
};
</script>
<style scoped>
* {
  box-sizing: border-box;
}

.user-hi h2 span{
  color: rgb(255, 94, 0);

}

.next {
  text-align: justify;
  margin: 10px auto;
  width: 70%;
}

.logout {
  background: #000;
  border: none;
  color: #eee;
  padding: 5px 8px;
  width: 150px;
  font-size: 18px;
}


</style>
