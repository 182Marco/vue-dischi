<template>
  <div v-show="showAll === true || album.like" class="wrap">
    <div class="box-img">
      <img :src="album.poster" :alt="album.title" />
    </div>
    <h3>{{ album.title }}</h3>
    <p>{{ album.author }}</p>
    <p>{{ album.year }}</p>
    <p>{{ album.genre }}</p>
    <i
      v-show="!album.like"
      @click="album.like = !album.like"
      class="far fa-star"
    ></i>
    <i
      v-show="album.like"
      @click="album.like = !album.like"
      class="fas fa-star"
    ></i>
  </div>
</template>

<script>
  export default {
    name: 'Disc',
    props: ['album', 'showAll'],
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .wrap {
    position: relative;
    text-align: center;
    img {
      width: 100%;
    }
  }

  .box-img {
    @include width-height(80%, 40%);
    overflow: hidden;
    margin: 10% auto 0;
    @include media-desk-first(l-tablet) {
      height: 48%;
    }
    @include media-desk-first(l-tablet) {
      height: 55%;
    }
    @include media-desk-first(s-tablet) {
      height: 65%;
    }
    @include media-desk-first(phone) {
      height: 60%;
    }
  }
  h3 {
    color: $light-txt;
    font-size: 0.9rem;
    font-weight: 300;
    text-transform: uppercase;
  }
  p {
    color: $grey-txt;
    font-size: 0.75rem;
    margin: 7px 0;
  }
  p:last-child {
    color: $light-txt;
  }
  i {
    position: absolute;
    left: 5%;
    bottom: 4%;
    color: $star;
    cursor: pointer;
  }
</style>
