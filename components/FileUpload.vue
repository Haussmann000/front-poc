<template>
  <div>
    <v-card-title class="headline">
      {{ ext.toUpperCase() }}ファイルをアップロード
    </v-card-title>
    <v-card-actions class="btn-wrapper">
      <v-btn
        :disabled="!files.length"
        color="primary"
      >
        <div>
          <p>Upload</p>
        </div>
      </v-btn>
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
<style scoped>
  html, body {
    margin: 0;
    padding: 0;
    font-family:'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
  }
  .headline {
    font-size: 3rem;
    margin: 0 auto;
    text-align: center;
    display: flex;
    justify-content: center;
    width: 100%;
    color: black;
    background-color:rgb(253, 229, 232);
  }
  .v-application p {
    margin-bottom: 0;
  }
  .drop-area {
    user-select: none;
    width: 80%;
    height: 200px;
    background-color: rgb(236, 237, 255);
    color: rgb(86, 86, 86);
    border-radius: 15px;
    margin: 15px;
    padding: 5px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: center;
    border: 3px dashed rgb(153, 207, 255);
    cursor: pointer;
  }
  .drop-area p {
    align-self: center;
  }
  .btn-wrapper, .v-sheet {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .enter.drop-area {
    border: 3px dashed rgb(50, 159, 255);
    background-color: rgb(209, 210, 235);
    color: rgb(128, 120, 120);
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
    color: green;
    padding-bottom: 10px;
  }

</style>
