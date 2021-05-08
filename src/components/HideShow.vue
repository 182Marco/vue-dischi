<template>
  <details>
    <summary> <h2>Click to see just the albums you like!</h2></summary>
    <div class="main-cont">
      <slot></slot>
    </div>
  </details>
</template>

<script>
  export default {
    name: 'HideShow',
    props: [],
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  h2 {
    display: inline-block;
  }
  h2,
  details {
    color: $light-txt;
  }

  summary {
    cursor: pointer;
  }
</style>
