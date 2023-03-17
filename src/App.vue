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
          <button v-if="submittedTitle" class="btn btn-secondary btn-block mt-3" @click="goToUrl">
            Go to URL with input text as ref parameter
          </button>
        </div>
      </div>
    </div>
    
    <!-- <footer class="container mt-5">
      <div class="row">
        <div class="col-md-12 text-center">
          <button class="btn btn-secondary" @click="toggleSound">
            Toggle Sound
          </button>
        </div>
      </div>
    </footer> -->
  </div>
</template>

<script>
import TextInput from "./components/TextInput.vue";
// import soundManager from "soundmanager2";


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
  // mounted() {
  //   this.setupSoundManager();
  // },
  methods: {
    onSubmit(apiResponse) {
      this.submittedTitle = apiResponse.title;
      this.submittedText = apiResponse.text;
      this.submittedImageUrl = apiResponse.imgUrl;
    },
    goToUrl() {
      // console.log(TextInput.inputText)
      // if (TextInput.inputText > 0) {
        // const refParam = encodeURIComponent(this.inputs.join(','));
        // window.location.href = `https://example.com?ref=${refParam}`;
        const url = `https://romanceradar.lightz.org/?ref=${encodeURIComponent(this.submittedTitle)}`;
        window.open(url, "_blank");
      // }
    },
    // setupSoundManager() {
    //   soundManager.setup({
    //     url: "/swf/",
    //     onready: () => {
    //       this.sound = soundManager.createSound({
    //         id: "backgroundSound",
    //         url: "https://cdn.mindverse.com/files/zzzz202301291674979007748%E8%83%8C%E6%99%AF%E9%9F%B3%E4%B9%90%E9%99%8D%E4%BD%8E%E9%9F%B3%E9%87%8F%E7%89%88.mp3",
    //         autoLoad: true,
    //         autoPlay: true,
    //         volume: 50,
    //       });
    //     },
    //   });
    // },
    // toggleSound() {
    //   if (this.sound) {
    //     if (this.sound.playState === 1) {
    //       this.sound.pause();
    //     } else {
    //       this.sound.play();
    //     }
    //   }
    // },
  },
};
</script>

<style>
/* Bootstrap styles */
.container {
  max-width: 600px;
  margin: 0 auto;
}
.input-group {
  margin-bottom: 1rem;
}
/* Custom styles */
body {
  background-color: rgb(156, 38, 156);
}
</style>