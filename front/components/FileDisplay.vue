<template>
  <div>
    <div class="display_area">
      <div class="fileListWrapper">
        <li v-for="filename,index in files" :key="index"  class="filename">
          <div class="fileNameList">
            <div v-if="files" class="fileIconWrapper">
              <img class="fileicon" src="@/assets/img/document_icon.png" alt="document icon">
            </div>
            <p class="fileNameText">
              {{ elipsisizeFileName(filename) }}
            </p>
            <div 
             class="deleteButton"
             @click="deleteItem(index)"
            >
              <img src="@/assets/img/delete.png" alt="">
            </div>
          </div>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
  const maxLength = 29;
	export default {
    name: 'FileDisplay',
    props: ['files'],
    data() {
      return {

      }
    },
    methods: {
    elipsisizeFileName(file) {
      const filename = file.name
      return filename.length < maxLength ? filename : `${filename.substr(0, maxLength)}...${filename.split(".").pop()}`
    },
    deleteItem(index) {
      this.files.splice(index, 1)
    },
    }
	}
</script>

<style scoped  lang="scss">
  .display_area {
    display: flex;
    flex-direction: center;
    justify-content: center;
  }
  .fileicon {
    width: 50px;
    display: inline;
  }
  .fileIconWrapper {
    background-color: white;
    border-radius: 50%;
    padding: 15px;
    margin: 5px;
  }
  .fileListWrapper {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
  }
  .filename {
    display: flex;
    margin: 15px;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
  .fileNameList {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    text-align: center;
    user-select: none;
    width: 100%;
    height: 100%;
    background-color: $pale-gray;
    padding: 15px;
    border-radius: 5px;
    cursor: pointer;
  }
  .fileNameText {
    white-space: nowrap;
    text-overflow: ellipsis;
    margin-bottom: 0;
  }
  li {
    list-style-type: none;
  }
  .fileNameList:hover {
    opacity: .6;
  }
  .deleteButton {
    width: 50px;
    height: 50px;
    margin-left: auto;
  }
  .deleteButton:hover {
    filter: contrast(10%)
  }
</style>
