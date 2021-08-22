<template>
  <div class="search">
    <div class="search__wrapper container-fluid">
      <input type="text" class="search__input" />
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.search {
  background: #e5e5e5;
  // display: flex;
  // justify-content: space-between;
  // align-items: flex-start;
  padding: 16px;
  &__wrapper {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding: 16px;
  }
  &__input {
    background: white;
    border: 1px solid #d5d5d5;
    border-radius: 4px;
    width: 700px;
    padding: 5px;
  }
}
</style>
