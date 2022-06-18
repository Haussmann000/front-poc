<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">

      <v-card>
        <v-card-title class="headline">
          顧客情報登録
        </v-card-title>
        
        <v-card-actions class="btn-wrapper">
          <v-btn>
            <input type="file" multiple>
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
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  name: 'Draggable',
  name: 'IndexPage',
  data() {
    return {
      drag: false,
      file: []
    }
  },
  methods: {
    drop(event) {
      this.drag = true
      const files = event.dataTransfer.files
      const reader = new FileReader()
      reader.onload = event => {
        this.file = event.target.result
      }
      reader.readAsDataURL(files[0])
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
  .drop-area {
    width: 80%;
    height: 200px;
    background-color: rgb(63, 71, 73);
    color: rgb(215, 247, 255);
    border-radius: 5px;
    margin: 15px;
    padding: 5px;
    text-align: center;
    display: flex;
    justify-content: center;
    align-content: center;
    border: 3px dashed rgb(24, 141, 173);
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
