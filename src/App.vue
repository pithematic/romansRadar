<!-- src/App.vue -->
<template>
  <div id="app">
    <TextInput @submit="onSubmit" />
    <div class="container mt-3">
      <div class="row">
        <div class="col-md-8 offset-md-2">
          <div v-if="submittedText || submittedImageUrl" class="my-2">
            <div class="card">
              <div class="card-body">
                <div v-if="submittedTitle" class="h2 text-center font-weight-bold mb-2">
                  {{ submittedTitle }}
                </div>
                <div v-if="submittedText">{{ submittedText }}</div>
                <div v-if="submittedImageUrl" class="text-center mt-3">
                  <img :src="submittedImageUrl" alt="Submitted image" class="img-fluid" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue";

export default {
  components: {
    TextInput,
  },
  data() {
    return {
      submittedTitle: "",
      submittedText: "",
      submittedImageUrl: "",
    };
  },
  methods: {
    onSubmit(apiResponse) {
      this.submittedTitle = apiResponse.title;
      this.submittedText = apiResponse.text;
      this.submittedImageUrl = apiResponse.imgUrl;
    },
  },
};
</script>
