<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">

      <v-card>
        <v-card-title class="headline">
          顧客情報登録
        </v-card-title>
        
        <v-card-actions class="btn-wrapper">
            <input type="file" >
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>

<style scoped>
  .btn-wrapper, .v-sheet {
    display: flex;
    justify-content: center;
    flex-direction: column;
  }
  .headline {
    margin: 0 auto;
  }

</style>
