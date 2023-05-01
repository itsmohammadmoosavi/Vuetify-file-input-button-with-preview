<template>
  <div>
    <v-col cols="12">
      <div
        style="
          background-color: #3e3e3e;
          text-align: center;
          padding: 10px;
          margin-bottom: 20px;
        "
      >
        <h3 style="color: #00ff03" class="text-body-2">
          THIS CODE 100% WORKS IN YOUR PROJECT
        </h3>
        <h4 class="text-body-2" style="color: #fff">
          in codesandbox use paperclip icon to see the result but in your
          project this icon is invisible and button works fine
        </h4>
      </div>
      <h4 class="text-body-1 font-weight-medium mb-3">
        Upload your Photo using Upload button
      </h4>
      <v-file-input
        v-model="selectedFile"
        accept="image/*"
        hide-input
        class="custom-upload"
      ></v-file-input>
    </v-col>
    <v-col cols="12" v-if="previewUrl">
      <h4 class="text-body-1 font-weight-medium mb-3">Uploaded Photo</h4>
      <v-img :src="previewUrl" class="uploaded-image">
        >
        <v-btn fab x-small class="upload-delete-btn" @click="selectedFile = ''"
          >X</v-btn
        ></v-img
      >
    </v-col>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFile: null,
    };
  },
  computed: {
    previewUrl() {
      if (this.selectedFile) {
        return URL.createObjectURL(this.selectedFile);
      } else {
        return "";
      }
    },
  },
};
</script>
<style scoped>
.custom-upload {
  background: #43368b;
  border-radius: 7px;
  color: white !important;
  text-align: center;
  margin: 10px 0;
  overflow: hidden;
}
.custom-upload::after {
  content: "Upload";
  text-align: center;
  margin: 0 auto;
  transform: translateX(-20px);
}
::v-deep .custom-upload .v-icon {
  opacity: 0 !important;
}
::v-deep .custom-upload .v-icon.v-icon.v-icon--link {
  padding: 100px 500px !important;
  z-index: 1 !important;
}
.upload-delete-btn {
  position: absolute;
  top: 0;
  left: 0;
  transform: translate(30%, 30%);
  font-size: 14px;
  background-color: crimson !important;
  color: white;
}
.uploaded-image {
  position: relative;
  width: 100%;
  border-radius: 10px;
  overflow: hidden;
}
</style>
