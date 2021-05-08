<template>
  <details>
    <summary>
      <h2>{{ title }}</h2></summary
    >
    <div class="main-cont">
      <slot></slot>
    </div>
  </details>
</template>

<script>
  export default {
    name: 'HideShow',
    props: ['title'],
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
