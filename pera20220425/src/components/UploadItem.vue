<script setup>
const props = defineProps({
  item: Object,
})
</script>

<template>
  <div class="upload-item-wrap">
    <img width="200" height="200" :src="item.base64src" />
  </div>
</template>

<style scoped>
.upload-item-wrap {
  width: 200px;
  height: 200px;
  border: 1px solid black;
}

img {
  object-fit: contain;
}
</style>
