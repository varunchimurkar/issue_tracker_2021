<template>
  <div class="card border-dark mb-3">
    <div class="card-header bg-transparent border-dark">
      Issue ID {{ issue.id }}
    </div>
    <div class="card-body text-success">
      <h6 class="card-status">{{ issue.status1 }}</h6>
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
};
</script>


<style>
.card-status {
  border-radius: 25px;
  background: #cecb1b;
  padding: 15px;
  width: 150px;
  color: black;
  text-align: center;
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
}
</style>