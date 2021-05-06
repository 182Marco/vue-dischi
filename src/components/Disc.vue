<template>
  <div class="wrap">
    <div class="box-img">
      <img :src="album.poster" :alt="album.title" />
    </div>
    <h2>{{ album.title }}</h2>
    <p>{{ album.author }}</p>
    <p>{{ album.year }}</p>
    <p>{{ album.genre }}</p>
  </div>
</template>

<script>
  export default {
    name: 'Disc',
    props: ['album'],
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .wrap {
    text-align: center;
    img {
      width: 100%;
    }
  }

  .box-img {
    @include width-height(80%, 40%);
    margin: 10% auto 0;
  }
  h2 {
    color: $light-txt;
    font-size: 0.9rem;
    font-weight: 300;
    text-transform: uppercase;
    margin-top: 20px 0 0;
  }
  p {
    color: $grey-txt;
    font-size: 0.75rem;
    margin: 7px 0;
  }
  p:last-child {
    color: $light-txt;
  }
</style>
