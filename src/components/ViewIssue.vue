<template>
  <div class="container">
    <div class="form-row">
      <div class="form-group col-md-3 mr-sm-3">
        <div class="style1">
          <label for="selected">Assignee</label>
          <div>
            <select v-model="selected" id="selected" class="form-control">
              <option value="">Select User</option>
              <option
                v-for="user in users"
                v-bind:name="user.name"
                :key="user.name"
              >
                {{ user.name }}
              </option>
            </select>
          </div>
        </div>
      </div>

      <div class="form-group col-md-3 mr-sm-3">
        <div class="style1">
          <label for="selectedstatus">Status</label>
          <div>
            <select
              v-model="selectedstatus"
              id="selectedstatus"
              class="form-control"
            >
              <option value="">Select Status</option>
              <option v-for="(s, i) in status" :key="i" :value="s.display_flag">
                {{ s.display_flag }}
              </option>
            </select>
          </div>
        </div>
      </div>
      <div class="form-group col-md-3 mr-sm-3">
        <div class="style1">
          <label>Due Date</label>
          <div class="date">
            <input
              type="date"
              class="form-control"
              id="dueDateFilter"
              placeholder="select"
            />
          </div>
        </div>

        <div v-for="issue in issues" :key="issue.id">
          <IssueCard
            @deleteuser="$emit('deleteuser', issue.id)"
            :issue="issue"
          />
        </div>
      </div>
    </div>
    <div v-if="issues.length < 1" class="text-center mt-5">
      No Issue Found ☕
    </div>
  </div>
</template>

<script>
import IssueCard from "./IssueCard";

export default {
  name: "ViewIssue",
  props: {
    users: Array,
    status: Array,
    issues: Array,
  },

  components: {
    IssueCard,
  },

  emits: ['deleteuser'],

  data() {
    return {
      selected: "",
      selectedstatus: "",
    };
  },

computed: {
    issuesW() {
      if (this.selectedstatus) {
        return this.issues.filter(
          (issue) => issue.status1 === this.selectedstatus
        );
      }
      return [];
    },
  },
  
};
</script>

<style>
.style1 {
  color: brown;
  margin-top: 45px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 1rem;
  font-weight: 450;
  line-height: 1.5;
  color: #212529;
  margin-left: 85px;
}
</style>