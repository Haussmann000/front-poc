<template>
  <div>
    <div class="display_area">
      <div class="fileListWrapper">
        <li v-for="value in files" :key="value" class="filename">
          <div v-if="files">
            <img class="fileicon" src="@/assets/img/document_icon.png" alt="document icon">
          </div>
          <div class="fileNameList">
            {{ value }}
          </div>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
	export default {
    name: 'FileDisplay',
    props: ['files'],
    data() {
      return {

      }
    },
    methods: {

    }
	}
</script>

<style scoped>
  .display_area {
    display: flex;
    flex-direction: center;
    justify-content: center;
  }
  .fileicon {
    width: 50px;
    display: inline;
  }
  .fileListWrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .filename {
    display: flex;
    margin: 15px;
    flex-direction: row;
  }
  .fileNameList {
    display: flex;
    align-items: center;
    justify-content: center;
    /* width: 300px; */
    /* white-space: pre-line; */
    height: 100%;
    background-color: #f5f5f5;
    padding: 15px;
    border-radius: 5px;
    cursor: pointer;
  }
  li {
    list-style-type: none;
  }
</style>
