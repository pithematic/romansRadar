<!-- src/components/TextInput.vue -->
<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8 offset-md-2">
        <div class="card my-3">
          <div class="card-body">
            <textarea
              class="form-control"
              placeholder="Enter text here"
              v-model="inputText"
              rows="5"
            ></textarea>
            <div class="text-center mt-3">
              <button
                class="btn btn-primary"
                type="button"
                @click="handleButtonClick"
              >
                Submit
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      inputText: "",
    };
  },
  methods: {
    async handleButtonClick() {
      try {
        const response = await axios.post(
          "https://bjeovandxk.execute-api.us-west-2.amazonaws.com/dev1",
          {
            text: this.inputText,
          }
        );
        this.$emit("submit", response.data);
      } catch (error) {
        console.error("API request failed:", error);
      }
    },
  },
};
</script>
