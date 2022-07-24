<template>
  <div class="header">
    <p>
      {{ title }}
    </p>
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
    display: flex;
    justify-content: center;
    align-items: center;
    height: 150px;
    margin-bottom: 60px;
    color: rgb(75, 75, 75);
    background-color: rgb(213, 215, 252);
    font-size: 2rem;
    text-align: center;
    padding: 24px;
    font-family: "Titillium Web"
  }
</style>
