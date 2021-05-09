<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'Header',
    props: [],
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';
  div {
    padding-right: 10px;
    background-color: $header-col;
    height: 9vh;
    @include flex(row, flex-start);
  }
</style>
