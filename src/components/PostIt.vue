<template>
  <div class="margin-top">
    <div class="container-fluid">
      <div class="row">
        <PostItKV
          size_class="col-6"
          v-bind:key_object="headers"
          title="Headers-"
        />
        <PostItKV
          size_class="col-6"
          v-bind:key_object="jsonBody"
          title="Body-"
        />
        <PostHTTP v-bind:headers="headers" v-bind:body="body" />
      </div>
    </div>
  </div>
</template>

<style>
.margin-top {
  margin-top: 80px;
}
</style>
<script>
import PostItKV from "./PostItKV";
import PostHTTP from "./PostHTTP";

export default {
  name: "PostIt",
  components: { PostItKV, PostHTTP },
  data: function() {
    return {
      headers: {},
      jsonBody: {},
      method: "",
      apiEndpoint: "",
      appMsg: "",
    };
  },
};
</script>
