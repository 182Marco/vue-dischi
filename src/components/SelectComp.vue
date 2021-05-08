<template>
  <div>
    <label for="choseType"></label>
    <select name="" id="choseType">
      <option>kind</option>
    </select>
  </div>
</template>

<script>
  export default {
    name: 'SelectComp',
    props: ['albums'],
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  div {
    background-color: red;
    height: 10vh;
  }
</style>
