<template>
  <div id="app">
    <search @filterUser="filterUser"></search>
    <spinner></spinner>
    <users :usersList="usersListAux"></users>
  </div>
</template>

<script>
import axios from "axios";
import Spinner from "./components/Spinner.vue";
import Users from "./components/Users.vue";
import Search from "./components/Search.vue";

export default {
  name: "app",
  components: {
    Spinner,
    Users,
    Search
  },
  data() {
    return {
      usersList: [],
      usersListAux: []
    };
  },
  methods: {
    filterUser: function(search) {
      this.usersListAux = [];
      for (var i = 0; i < this.usersList.length; i++) {
        if (this.usersList[i].name.toLowerCase().includes(search.toLowerCase())) {
          this.usersListAux.push(this.usersList[i]);
        }
      }
    },
    getUsers() {
      axios
        .get("https://jsonplaceholder.typicode.com/users")
        .then(response => {
          document.getElementById("js-spinner").style.opacity = "0";
          document.getElementById("js-content").style.opacity = "1";
          this.usersList = response.data;
          this.usersListAux = response.data;
        })
        .catch(function(error) {
          console.log("error", error);
        });
    }
  },
  mounted() {
    this.getUsers();
  }
}
</script>
