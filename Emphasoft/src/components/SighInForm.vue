<template>
  <div class="content_form">
    <form action>
      <span>Log in</span>
      <div>
        <input type="text" v-model="data.username" />
      </div>
      <div>
        <input type="text" v-model="data.password" />
      </div>
      <div>
        <button type="button" v-on:click="getToken">Sign in</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      token: "",
      data: {
        username: "",
        password: "",
      },
    };
  },
  methods: {
    getToken() {
      let url =
        "http://emphasoft-test-assignment.herokuapp.com/api-token-auth/";
      const str = JSON.stringify(this.data);
      axios
        .post(url, str, {
          headers: {
            accept: "application/json",
            "Content-type": "application/json",
          },
        })
        .then((response) => {
          this.token = response.data.token;
          this.$emit("getData", this.token);
        })
        .catch((error) => {
          console.log(error);
          alert("Введен неверный логин или пароль!");
        });
    },
  },
};
</script>

<style>
.content_form {
  margin-top: 15%;
}
</style>