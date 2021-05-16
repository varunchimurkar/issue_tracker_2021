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

                <div class="modal-body__form">
                  <div class="form-group">
                    <label for="issue_summary">Summary</label>
                    <input
                      type="text"
                      class="form-control"
                      id="issueSummary"
                      placeholder="Issue Summary"
                      v-model="summary"
                      required
                      @change="validateInput"
                    />
                    <div class="invalid-feedback"></div>
                  </div>

                  <div class="form-row">
                    <div class="form-group col-md-6 pr-md-4">
                      <label for="selectSeverity">Severity</label>
                      <select
                        class="form-control custom-select"
                        id="selectSeverity"
                        v-model="severity"
                        @change="validateInput"
                        required
                      >
                        <option value="" disabled selected>
                          Select Severity
                        </option>
                        <option value="high">High</option>
                        <option value="medium">Medium</option>
                        <option value="low">Low</option>
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
                        @change="validateInput"
                        required
                      />
                      <div class="invalid-feedback"></div>
                    </div>
                  </div>

                  <div class="form-row">
                    <div class="form-group col-md-6 pr-md-4">
                      <label for="selectUser">Assigned To</label>
                      <select
                        class="form-control custom-select"
                        id="selectUser"
                        v-model="assignedTo"
                        @change="validateInput"
                        required
                      >
                        <option value="" disabled selected>Select User</option>
                        <option
                          v-for="user in usersList"
                          :key="user.id"
                          :value="user.id"
                        >
                          {{ user.name }}
                        </option>
                      </select>
                      <div class="invalid-feedback"></div>
                    </div>

                    <div class="form-group col-md-6 pl-md-4">
                      <label for="selectStatus">Status</label>
                      <select
                        class="form-control custom-select"
                        id="selectStatus"
                        v-model="status"
                        @change="validateInput"
                        required
                      >
                        <option value="" disabled selected>
                          Select Status
                        </option>
                        <option
                          v-for="(s, i) in statusList"
                          :key="i"
                          :value="s.flag"
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
                      @change="validateInput"
                      required
                    ></textarea>
                    <div class="invalid-feedback"></div>
                  </div>
                </div>

                <div class="modal-body__actions">
                  <button
                    type="button"
                    @click="resetModalFields"
                    class="btn close-btn"
                    data-dismiss="modal"
                  >
                    Close
                  </button>

                  <button type="button" class="btn save-btn" @click="saveIssue">
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
</style>
