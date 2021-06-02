<template>
  <div class="card border-dark mb-3">
    <div class="card-header bg-transparent border-dark">
      Issue ID {{ issue.id }}
    </div>
    <div class="card-body text-success">
      <h6 class="card-status">{{ issue.status1 }}</h6>
      <span>
        <button @click="onDelete(issue.id)" class="btndelete">Delete</button>
      </span>
      &nbsp;
      <span> <button class="btnclose">Close</button> </span>

      <br />
      <br />
      <p class="card-summary">{{ issue.summary }}</p>
      <p class="card-description">{{ issue.description }}</p>
    </div>
    <div class="card-footer bg-transparent border-dark">
      <div>
        <font-awesome-icon :icon="['fas', 'flag']" />
        {{ issue.severity }}
        <font-awesome-icon :icon="['fas', 'clock']" />
        {{ issue.dueDate }}
        <font-awesome-icon :icon="['fas', 'user']" />
        {{ issue.assignedTo }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IssueCard",

  props: {
    issue: Object,
  },

  methods: {
    onDelete(id) {
      this.$emit("delete-user", id);
    },
  },
};
</script>


<style>
.card-status {
  border-radius: 20px;
  background: #2bca7a;
  padding: 8px;
  width: 115px;
  color: black;
  text-align: center;
  display: inline-block;
}

.card {
  opacity: 0.5;
}

.card:hover {
  opacity: 1;
}

.card {
  margin-left: -188%;
  margin-top: 30%;
  width: 290%;
  display: flex;
}

.card-summary {
  color: black;
}

.card-description {
  color: black;
}

.btnclose {
  width: 80px;
  height: 35px;
  background-color: rgb(233, 197, 38);
  border: none;
  margin-left: 61%;
}

.btndelete {
  width: 80px;
  height: 35px;
  background-color: rgb(230, 83, 39);
  border: none;
  float: right;
}
</style>