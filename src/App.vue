<template>
  <div>
    <Header />
    <AddnewIssue
      title="All Issues"
      :users="users"
      :status="status"
      @addNewIssue="add"
    />
    <ViewIssue
      :users="users"
      :status="status"
      :issues="issues"
      @deleteuser="DeleteUser" 
      
    />
    <IssueCard :issues="issues" />
  </div>
</template>

<script>
import Header from "./components/Header";
import AddnewIssue from "./components/AddnewIssue";
import ViewIssue from "./components/ViewIssue";
import IssueCard from "./components/IssueCard";

export default {
  name: "App",
  components: {
    Header,
    AddnewIssue,
    ViewIssue,
    IssueCard,
  },
  data() {
    return {
      users: [
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
      ],

      status: [
        {
          flag: "to_do",
          display_flag: "To Do",
        },
        {
          flag: "in_progress",
          display_flag: "In Progress",
        },
        {
          flag: "done",
          display_flag: "Done",
        },
        {
          flag: "close",
          display_flag: "Close",
        },
      ],

      issues: [],
    };
  },

  methods: {
    add(IssueCard) {
      this.issues = [...this.issues, IssueCard];
    },

    DeleteUser(id) {
      this.issues = this.issues.filter((issue) => issue.id !== id);
    },
  },

  watch: {
    issues(newValue) {
      localStorage.setItem("issues", JSON.stringify(newValue));
    },
  },
  mounted() {
    this.issues = JSON.parse(localStorage.getItem("issues")) || [];
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
