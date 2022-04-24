<template>
  <label for="upload-input">
    <span>
      <i class="fa-solid fa-file-circle-plus"></i>
      ファイルを選択する
    </span>
  </label>
  <input
    id="upload-input"
    type="file"
    placeholder="ファイルを選択する"
    multiple
    @change="(e) => $emit('Change', e)"
  />
</template>

<style scoped>
label {
  padding: 1px 6px;
  border: 1px solid #000000;
  border-radius: 4px;
  display: inline-block;
  background-color: #dcdcdc;
  cursor: pointer;
}

label > span {
  font-size: 14px;
  display: inline-block;
  line-height: 20px;
}

input {
  display: none;
}
</style>
