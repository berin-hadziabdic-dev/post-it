<template>
  <div class="col-12 col-md-6">
    <div class="row">
      <h2 class="text-warning">{{ title + "JSON" }}</h2>
      <div class="col-12">
        <span v-if="!validInput" class="text-danger"
          >The app does not allow empty strings as inputs to header/json
          property key-values.</span
        >
        <span v-else class="text-success"> Input good.</span>
      </div>
      <div class="col-12 col-md-6 form-group">
        <label for="header-name">Key-Name</label>
        <input
          type="text"
          v-model="key"
          placeholder="key-input"
          class="form-control"
        />
      </div>
      <div class="col-12 col-md-6 form-group">
        <label for="header-name">Key-Value</label>
        <input
          type="text"
          v-model="value"
          placeholder="value-input"
          class="form-control"
        />
      </div>
      <div class=" col-sm-12 col-md-3 form-group">
        <input
          type="button"
          value="Add-KV-Pair"
          class="btn btn-primary"
          v-on:click="addToKeyValueObject"
        />
      </div>
      <div class="col-12 print-area">
        <h2 class="text-success">{{ title }}-JSON-String</h2>
        <pre> <p class="text-success">{{ stringifyFunction() }}</p></pre>
      </div>
    </div>
  </div>
</template>

<style>
.print-area {
  height: 300px;
  overflow-y: scroll;
}
</style>

<script>
export default {
  name: "PostItKV",
  props: ["key_object", "title"],
  data: function() {
    return {
      key: "",
      value: "",
      validInput: true,
    };
  },
  methods: {
    validKV: function() {
      let keyChecks =
        typeof this.key === "string" &&
        this.key !== "" &&
        this.key !== undefined &&
        this.key !== null;
      let valueChecks =
        typeof this.value === "string" &&
        this.value !== "" &&
        this.value !== undefined &&
        this.value !== null;

      return keyChecks & valueChecks;
    },
    addToKeyValueObject: function() {
      if (this.validKV()) {
        this.key_object[this.key] = this.value;
        this.key = "";
        this.value = "";
        this.validInput = true;
      } else {
        this.validInput = false;
      }
    },
    stringifyFunction: function() {
      return JSON.stringify(this.key_object, null, 2);
    },
  },
};
</script>
