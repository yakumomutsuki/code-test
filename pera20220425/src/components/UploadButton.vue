<template>
  <button @click="$emit('onClick')">保存</button>
</template>

<style scoped>
button {
  color: white;
  background-color: rgb(3, 213, 172);
  border: none;
  border-radius: 4px;
  width: 300px;
  box-shadow: none;
  cursor: pointer;
}
</style>
