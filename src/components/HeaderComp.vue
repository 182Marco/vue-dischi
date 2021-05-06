<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: 'Header',
    props: {
      // msg: String,
    },
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';
  div {
    background-color: $header-col;
    height: 9vh;
    @include flex(row, flex-start);
    margin-bottom: 13vh;
  }
</style>
