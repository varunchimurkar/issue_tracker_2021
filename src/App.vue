<template>
  <div>
    <Header />
    <AddnewIssue title="All Issues" :users="users" :status="status" @addNewIssue="add"/>
    <ViewIssue :users="users" :status="status" :issues="issues"/>
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
        flag: 'to_do',
        display_flag: 'To Do',
        color_class: 'secondary',
      },
      {
        flag: 'in_progress',
        display_flag: 'In Progress',
        color_class: 'primary',
      },
      {
        flag: 'done',
        display_flag: 'Done',
        color_class: 'success',
      },
      {
        flag: 'close',
        display_flag: 'Close',
        color_class: 'info',
      },
      ],

      issues: [],
    };
  },

  methods: {
    add(IssueCard)  {
      this.issues = [...this.issues, IssueCard]
    },
  }

 

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
