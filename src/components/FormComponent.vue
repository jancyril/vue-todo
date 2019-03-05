<template>
  <div class="row">
    <div class="col-12">
      <div class="alert alert-danger" v-show="contentIsEmpty" role="alert">Description is required.</div>
      <form @submit.prevent="itemSubmitted">
        <div class="form-group">
          <label for="description">Description</label>
          <textarea
            id="description"
            class="form-control"
            rows="3"
            v-model="contents"
            placeholder="Enter your todo things"
          ></textarea>
        </div>
        <div class="form-group text-right">
          <button type="submit" class="btn btn-primary mb-2">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contents: "",
      contentIsEmpty: false
    };
  },

  methods: {
    itemSubmitted() {
      if (!this.contents) {
        this.contentIsEmpty = true;
        return;
      }

      this.contentIsEmpty = false;
      this.$emit("itemSubmitted", this.contents);
      this.contents = "";
    }
  }
};
</script>
