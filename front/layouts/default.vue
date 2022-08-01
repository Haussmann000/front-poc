<template>
  <v-app>
    <Header :title="title"></Header>
      <v-container>
        <Nuxt />
      </v-container>
  </v-app>
</template>

<script>

import Header from './Header.vue'

export default {
  methods: {
  },
  components: {
    Header,
  },
  name: 'DefaultLayout',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      title: 'FileUploader'
    }
  }
}
</script>
