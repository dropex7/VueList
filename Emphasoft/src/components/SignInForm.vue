<template>
  <div class="content_form">
    <form action>
      <span>
        <h2>Login</h2>
      </span>
      <div class="content_form_input">
        <input id="textInputUsername" type="text" v-model="data.username" placeholder="Username..." />
      </div>
      <div class="content_form_input">
        <input
          id="textInputPassword"
          type="password"
          v-model="data.password"
          placeholder="Password..."
        />
      </div>
      <div>
        <button class="content_form_btn" type="button" v-on:click="getToken">Sign in</button>
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
          document.getElementById("textInputUsername").value = "";
          document.getElementById("textInputPassword").value = "";
        });
    },
  },
};
</script>

<style>
.content_form {
  margin-top: 15%;
}
h2 {
  margin: 10px;
}
.content_form_input {
  font-size: 14px;
  margin: 6px 0;
}
.content_form_input input {
  padding: 5px 30px;
  color: #f8f8f8;
  background-color: #44475a;
  border: none;
  border-radius: 5%;
}

.content_form_input input:focus {
  outline: none;
  border: 1px solid #f8f8f8;
}
.content_form_btn {
  margin-top: 5px;
  background-color: #44475a;
  border-radius: 6%;
  border-color: #f8f8f8;
  color: #f8f8f8;
  padding: 7px 20px;
  width: 100px;
}

.content_form_btn:hover {
  background-color: #8be9fd;
  color: #44475a;
}
</style>