<template>
  <div class="container">
    <div class="form-row">
      <div class="form-group col-md-3 mr-sm-3">
        <div class="style1">
          <label>Assignee</label>
          <div>
            <select v-model="selected" class="form-control">
              <option disabled value="">Select user</option>
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
          <label>Status</label>
          <div>
            <select v-model="selected" class="form-control">
              <option disabled value="">Select user</option>
              <option
                v-for="user in status"
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
          <label>Due Date</label>
          <div class="date">
            <input
              type="date"
              class="form-control"
              id="dueDateFilter"
              placeholder="select"
              v-model="dueDateFilter"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="text-center mt-5">No Issue Found ☕</div>
  </div>
</template>

<script>
export default {
  name: "ViewIssue",
  props: {
    users: Array,
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