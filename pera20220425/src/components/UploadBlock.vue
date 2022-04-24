<script setup>
import { reactive } from 'vue'
import UploadButton from './UploadButton.vue'
import UploadInput from './UploadInput.vue'
import UploadItem from './UploadItem.vue'

const defaultUploadItemState = {
  base64src: '',
}
const state = reactive({
  uploadItems: [],
})

const onClick = () => {
  console.log('aaa')
}

const onChangeInput = (e) => {
  const { files } = e.target
  Array.from(files).forEach((file) => {
    const reader = new FileReader()
    reader.readAsDataURL(file)
    reader.onload = (e) => {
      const uploadItemState = structuredClone(defaultUploadItemState)
      uploadItemState.base64src = e.target.result
      state.uploadItems.push(uploadItemState)
    }
  })
}
</script>

<template>
  <div class="wrapper">
    <div class="side-nav">
      <p>商品写真</p>
    </div>
    <div class="main">
      <div class="items-wrap">
        <UploadItem
          v-for="(item, index) in state.uploadItems"
          :key="`upload-item-${index}`"
          :item="item"
        />
      </div>

      <div class="upload-input-wrap">
        <UploadInput @change="onChangeInput" />
      </div>

      <div class="upload-button-wrap">
        <UploadButton @click="onClick" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  display: flex;
}

.side-nav {
  background-color: #dcdcdc;
  min-height: 40px;
  min-width: 200px;
}

.side-nav p {
  margin-top: 20px;
}

.main {
  display: flex;
  flex-direction: column;
  min-width: 400px;
}

.items-wrap {
  display: flex;
  flex-wrap: wrap;
}

.items-wrap .upload-item-wrap {
  margin: 0 20px 20px 20px;
}

.upload-input-wrap {
  text-align: left;
  margin-left: 20px;
  margin-bottom: 40px;
}

.upload-button-wrap {
  text-align: center;
  margin-bottom: 40px;
}

@media screen and (max-width: 420px) {
  .wrapper {
    flex-direction: column;
  }

  .side-nav {
    margin-bottom: 20px;
  }

  .main {
    width: auto;
  }

  .items-wrap {
    justify-content: center;
  }
}
</style>
