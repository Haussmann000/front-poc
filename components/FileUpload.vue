<template>
  <div>
        <v-card-actions class="btn-wrapper">
          <v-btn>
            <div class="upload">
              <p>
                Upload
              </p>
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
            CSVファイルをドラッグしてください
          </p>
          </div>
        </v-card-actions>
        <FileDisplayVue :files="files"></FileDisplayVue>
  </div>
</template>
<script>
import FileDisplayVue from './FileDisplay.vue'
export default {
  props: {
  },
  name: 'Draggable',
  name: 'FileUpload',
  name: 'FileDisplay',
  components: {
    FileDisplayVue
  },
  data() {
    return {
      drag: false,
      files: [],
    }
  },
  methods: {
    display(files) {
      Array.from(files).forEach(file => {
        this.files.push(file.name)
      })
    },
    drop(event) {
      this.drag = true
      const files = event.dataTransfer.files
      this.display(files)
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
  .v-application p {
    margin-bottom: 0;
  }
  .drop-area {
    width: 80%;
    height: 200px;
    background-color: rgb(0, 5, 100);
    color: rgb(215, 247, 255);
    border-radius: 15px;
    margin: 15px;
    padding: 5px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: center;
    border: 3px dashed aliceblue;
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
    border: 2px dashed #1867c0;
    background: #d4e8ff;
  }
  .headline {
    font-size: 3rem;
    margin: 0 auto;
  }

</style>
