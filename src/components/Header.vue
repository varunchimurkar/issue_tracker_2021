<template>
  <div class="container">
    <b-navbar toggleable="sm" type="light" variant="light">
      <b-navbar-toggle target="navbar-toggle-collapse"></b-navbar-toggle>
      <b-navbar-brand
        ><img
          src="favicon.svg"
          class="d-inline-block align-middle"
          alt="logo"
        />
        <span class="d-inline-block align-middle m-2">IssueTracker</span>
      </b-navbar-brand>
      <b-collapse id="navbar-toggle-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item>Home</b-nav-item>
          <b-nav-item>About</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
.ml-auto {
  font-size: 12px;
  font-family: fangsong;
}

.d-inline-block {
  color: black;
  font-family: cursive;
}
</style>
