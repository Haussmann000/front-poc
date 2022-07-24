<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>        
        <FileUpload></FileUpload>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
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
</style>
