<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">

      <v-card>
        <v-card-title class="headline">
          情報登録
        </v-card-title>
        
        <FileUpload></FileUpload>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import draggable from 'vuedraggable'
import FileUpload from '../components/FileUpload.vue'
export default {
    name: "Draggable",
    name: "IndexPage",
    data() {
        return {
            drag: false,
            file: []
        };
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
  }

</style>
