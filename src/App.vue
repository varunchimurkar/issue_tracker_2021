<template>
  <div>
    <Header />
    <AddnewIssue title="All Issues" />
    <ViewIssue :users="users" />
  </div>
</template>

<script>
import Header from "./components/Header";
import AddnewIssue from "./components/AddnewIssue";
import ViewIssue from "./components/ViewIssue";

export default {
  name: "App",
  components: {
    Header,
    AddnewIssue,
    ViewIssue,
  },
  data() {
    return {
      users: [],
    };
  },

  created() {
    this.users = [
      {
        id: 1,
        name: "Luc Hurst",
      },
      {
        id: 2,
        name: "Carl Boyce",
      },
      {
        id: 3,
        name: "Luis Marsh",
      },
      {
        id: 4,
        name: "Harlen Gill",
      },
      {
        id: 5,
        name: "Laura Morgan",
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
