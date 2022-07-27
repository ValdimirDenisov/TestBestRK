<template>
  <input type="text" class="search_input" placeholder="Поиск по всем категориям">
</template>

<script>
export default {
  name: "MyInput"
}
</script>

<style scoped lang="scss">
  .search_input {
    width: calc(100% - 40px);
    border-radius: 5px;
    font-size: 14px;
    height: 30px;
    border: 2px solid #8f8f8f;
    margin: 10px auto auto;
  }

  .search_input:focus {
    outline: none
  }

  .search_input[placeholder] {
    text-overflow: ellipsis;
    padding: 5px 10px;
  }
</style>
