<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <h1 class="app-header col-12">Post-It</h1>
      </div>
      <PostIt />
    </div>
  </div>
</template>

<style>
.app-header {
  top: 0;
  left: 0;
  position: fixed;
  height: 80px;
  background: slategray;
  color: white;
  width: 100vh;
}
</style>
<script>
import PostIt from "./components/PostIt";
export default {
  name: "App",
  components: {
    PostIt,
  },
};
</script>
