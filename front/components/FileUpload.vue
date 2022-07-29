<template>
  <div class="fileUploadWrapper">
    <v-card-title class="headline">
      {{ ext.toUpperCase() }}ファイルをアップロード
    </v-card-title>
    <v-card-actions class="btn-wrapper">

      <div
        class="drop-area"
        @dragenter="drag = true"
        @dragover.prevent="drag = true"
        @drop.prevent="drop"
        @dragleave="dragleave()"
        :class="{ enter: drag }"
      >
      <p>
        ファイルをドラッグしてください
      </p>
      </div>
    </v-card-actions>
    <FileDisplayVue :files="files" />
    <div class="alertArea">
      <p class="alertText">
        {{ alertMessage }}
      </p>
    </div>
    <v-btn
        :disabled="!files.length"
        color="primary"
      >
        <div>
          <p>Upload</p>
        </div>
      </v-btn>
  </div>
</template>
<script>
import FileDisplayVue from './FileDisplay.vue'
export default {
  name: 'FileUpload',
  name: 'FileDisplay',
  components: {
    FileDisplayVue
  },
  data() {
    return {
      drag: false,
      files: [],
      alertMessage: "",
      ext: "csv",
    }
  },
  methods: {
    checkExt(file) {
      const allowedFileExt = `.*\.${this.ext}$`
      return file.match(allowedFileExt)
    },
    toggleMessage() {
      return !this.files.length ? `アップロードできるのは${this.ext}ファイルのみです` : ""
    },
    drop(event) {
      this.drag = true
      const files = event.dataTransfer.files
      this.files = Array.from(files).filter(e => this.checkExt(e.name))
      this.alertMessage = this.toggleMessage()
      const reader = new FileReader()
      reader.onload = event => {
        this.file = event.target.result
      }
      // reader.readAsDataURL(files[0])
      this.drag = false
    },
    dragleave() {
      this.drag = false
      this.file = []
    }
}
}
</script>
<style scoped lang="scss">
  html, body {
    margin: 0;
    padding: 0;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
  }
  .fileUploadWrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;

  }
  .headline {
    font-size: 3rem;
    margin: 0 auto;
    text-align: center;
    display: flex;
    justify-content: center;
    width: 100%;
    color: $dark-gray;
    background-color:$pale-white;
    border-radius: 5px;
  }
  .v-application p {
    margin-bottom: 0;
  }
  .drop-area {
    user-select: none;
    width: 80%;
    height: 200px;
    background-color: $pale-white;
    color: $dark-gray;
    border-radius: 15px;
    margin: 15px;
    padding: 5px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: center;
    border: 3px dashed $root-blue;
    cursor: pointer;
    &p {
       align-self: center;
    }
    &.enter {
      border: 3px dashed $root-blue;
      background-color: $pale-blue;
      color: $root-gray;
    }
  }
  .btn-wrapper, .v-sheet {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .headline {
    font-size: 3rem;
    margin: 0 auto;
  }

  .alertArea {
    display: flex;
    justify-content: center;
  }
  .alertText {
    color: $root-green;
    padding-top: 10px;
    padding-bottom: 10px;
  }

</style>
