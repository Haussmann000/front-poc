<template>
  <div class="header">
    {{ title }}
  </div>
</template>

<script>
	export default {
    name: "Header",
    props: ['title'],
    data() {
      return {

      }
    }
	}
</script>

<style>
  .header {
    color: rgb(75, 75, 75);
    background-color: #f5f5f5;
    font-size: 2rem;
    text-align: center;
    padding: 10px;
    font-family: "Titillium Web"
  }
</style>
