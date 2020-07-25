<template>
  <div class="container_login">
    <SignInForm v-if="!isAccessed" v-on:getData="getData($event)" />
    <div v-else-if="isAccessed">
      <ListOfUsers
        v-on:sortById="sortById"
        v-on:sortByUsername="sortByUsername"
        v-bind:dataUsers="dataUsers"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SignInForm from "./SignInForm";
import ListOfUsers from "./ListOfUsers";
export default {
  data() {
    return {
      dataUsers: [],
      isAccessed: false,
      sortNameState: true,
      sortIdState: true,
    };
  },
  components: {
    SignInForm,
    ListOfUsers,
  },
  methods: {
    getData(token) {
      let url = "http://emphasoft-test-assignment.herokuapp.com/api/v1/users/";
      axios
        .get(url, {
          headers: {
            accept: "application/json",
            Authorization: "Token " + token,
            "X-CSRFToken":
              "v2b6UGVmIBdg6N8YzWb1G4eYQyfOZNplcdfPxwR79YOyWpHjPmpKcRocCjKTSLCe",
          },
        })
        .then((response) => {
          this.isAccessed = true;
          this.dataUsers = response.data;
        });
    },
    sortByUsername() {
      if (this.sortNameState) {
        this.sortNameState = false;
        this.dataUsers.sort((a, b) => {
          if (a.username > b.username) {
            return 1;
          } else if (a.username < b.username) {
            return -1;
          } else return 0;
        });
      } else {
        this.sortNameState = true;
        this.dataUsers.sort((a, b) => {
          if (a.username > b.username) {
            return -1;
          } else if (a.username < b.username) {
            return 1;
          } else return 0;
        });
      }
    },
    sortById() {
      if (this.sortIdState) {
        this.sortIdState = false;
        this.dataUsers.sort((a, b) => {
          return a.id - b.id;
        });
      } else {
        this.sortIdState = true;
        this.dataUsers.sort((a, b) => {
          return b.id - a.id;
        });
      }
    },
  },
};
</script>

<style>
</style>

