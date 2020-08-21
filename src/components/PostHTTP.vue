<template>
  <div class="row">
    <div class="form-group col-4">
      <label for="methods">HTTP methods</label>
      <select id="methods" v-model="method" class="form-control">
        <option value="GET">GET</option>
        <option value="PUT">PUT</option>
        <option value="POST">POST</option>
        <option value="DELETE">DELETE</option>
      </select>
    </div>
    <div class="form-group col-4">
      <label for="endpoint">API-Endpoint</label>
      <input
        id="endpoint"
        placeholder="/Apiendpoint"
        type="text"
        v-model="endpoint"
        class="form-control"
      />
    </div>
    <div class="form-group col-4">
      <label for="btn-http text-white">.</label>
      <input type="button" value="Send Msg To Server" class="btn btn-success" />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PostHTTP",
  props: ["headers", "body"],
  data: function() {
    return {
      method: "GET",
      endpoint: "",
      responseMsg: "",
    };
  },
  methods: {
    axiosHttp: function() {
      let options = {
        url: this.endpoint,
        headers: this.headers,
        body: this.body,
        validateStatus: true,
        timeout: 4000,
      };
      axios(options).then(
        (resp) => {
          if (resp.status === 200) {
            this.responseMsg = resp.data;
          }
        },
        (err) => {
          this.responseMsg = err;
        }
      );
    },
  },
};
</script>
