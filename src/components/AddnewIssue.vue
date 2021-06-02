<template>
  <div>
    <div class="addnew">
      <br />
      <br />
      <div class="title">
        <h5>{{ title }}</h5>
        <!-- <button class="btn">Add New Issues</button> -->

        <div
          class="modal fade"
          id="addNewIssueModal"
          tabindex="-1"
          aria-labelledby="addNewIssueModal"
          aria-hidden="true"
        >
          <div class="modal-dialog modal-lg">
            <div class="modal-content">
              <div class="modal-body">
                <div class="modal-body__title">Add New Issue</div>
                <br />

                <div class="modal-body__form">
                  <div class="form-group">
                    <label for="issue_summary">Summary</label>
                    <input
                      type="text"
                      class="form-control"
                      id="issueSummary"
                      placeholder="Issue Summary"
                      v-model="summary"
                    />
                    <div class="invalid-feedback"></div>
                  </div>

                  <div class="form-row">
                    <div class="form-group col-md-6 pr-md-4">
                      <label for="selectSeverity">Severity</label>
                      <select
                        class="form-control"
                        id="selectSeverity"
                        v-model="severity"
                      >
                        <option value="" disabled selected>
                          Select Severity
                        </option>
                        <option value="High">High</option>
                        <option value="Medium">Medium</option>
                        <option value="Low">Low</option>
                      </select>
                      <div class="invalid-feedback"></div>
                    </div>

                    <div class="form-group col-md-6 pl-md-4">
                      <label for="selectDueDate">Due Date</label>
                      <input
                        type="date"
                        class="form-control"
                        id="selectDueDate"
                        placeholder="select"
                        v-model="dueDate"
                      />
                      <div class="invalid-feedback"></div>
                    </div>
                  </div>

                  <div class="form-row">
                    <div class="form-group col-md-6 pr-md-4">
                      <label for="selectUser">Assigned To</label>
                      <select
                        class="form-control"
                        id="selectUser"
                        v-model="assignedTo"
                      >
                        <option value="" disabled selected>Select User</option>
                        <option
                          v-for="user in users"
                          v-bind:name="user.name"
                          :key="user.name"
                        >
                          {{ user.name }}
                        </option>
                      </select>
                      <div class="invalid-feedback"></div>
                    </div>

                    <div class="form-group col-md-6 pl-md-4">
                      <label for="selectStatus">Status</label>
                      <select
                        class="form-control"
                        id="selectStatus"
                        v-model="status1"
                      >
                        <option value="" disabled selected>
                          Select Status
                        </option>
                        <option
                          v-for="(s, i) in status"
                          :key="i"
                          :value="s.display_flag"
                        >
                          {{ s.display_flag }}
                        </option>
                      </select>
                      <div class="invalid-feedback"></div>
                    </div>
                  </div>

                  <div class="form-group">
                    <label for="issueDescription">Description</label>
                    <textarea
                      class="form-control"
                      id="issueDescription"
                      placeholder="Describe the issue..."
                      rows="4"
                      v-model="description"
                    ></textarea>
                    <div class="invalid-feedback"></div>
                  </div>
                </div>

                <div class="modal-body__actions">
                  <button
                    type="button"
                    class="btnn close-btn"
                    data-dismiss="modal"
                  >
                    Close
                  </button>

                  <button
                    type="button"
                    class="btnn save-btn"
                    @click="saveIssue"
                  >
                    Save Issue
                  </button>

                  <div class="clearfix"></div>
                </div>

                <div id="saveBtnFeedback" class="float-right mt-2"></div>
                <div class="clearfix"></div>
              </div>
            </div>
          </div>
        </div>

        <button class="btn" data-toggle="modal" data-target="#addNewIssueModal">
          Add New Issue
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddnewIssue",
  props: {
    title: String,
    users: Array,
    status: Array,
  },

  data() {
    return {
      summary: null,
      severity: "",
      dueDate: null,
      assignedTo: "",
      status1: "",
      description: null,
    };
  },

  methods: {
    saveIssue(e) {
      e.preventDefault();

      if (
        !this.summary ||
        !this.description ||
        !this.dueDate ||
        this.status1 === "" ||
        this.assignedTo === "" ||
        this.severity === ""
      ) {
        alert("Please fill all input fields");
        return;
      }

      const newload = {
        id: Math.floor(Math.random() * 100000000000),
        summary: this.summary,
        severity: this.severity,
        dueDate: this.dueDate,
        assignedTo: this.assignedTo,
        status1: this.status1,
        description: this.description,
      };

      console.log(newload);

      this.$emit("addNewIssue", newload);

      this.id = "";
      this.summary = "";
      this.severity = "";
      this.dueDate = "";
      this.assignedTo = "";
      this.status1 = "";
      this.description = "";
    },
  },
};
</script>

<style>
.addnew {
  background-color: rgb(28, 74, 173);
  width: 100%;
  height: 130px;
  color: white;
}
.title {
  margin-left: 140px;
}

.btn {
  display: inline-block;
  background: dodgerblue;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  margin-left: 75%;
  margin-top: -3%;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:hover {
  background-color: white;
  color: black;
}

.btnn {
  border-radius: 3px;
  font-family: inherit;
  padding: 0.7em 2em;
  margin-top: 9px;
}
.close-btn {
  background-color: #0c0c0c;
  border: 1px solid #fafcfd;
  color: #fafbfc;
}

.save-btn {
  float: right;
  background-color: #08a55d;
  border: 1px solid #08a55d;
  color: #ffffff;
}

.modal-body {
  color: #08090a;
  font-family: "Times New Roman", Times, serif;
}

.modal-body__title {
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  font-size: 18px;
}
</style>
