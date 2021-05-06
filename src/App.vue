<template>
  <div id="app">
    <HeaderComp>
      <img class="header-logo" src="@/assets/logo.png" alt="logo" />
    </HeaderComp>
    <div class="main-cont">
      <Disc
        v-for="(album, i) in albums"
        :key="i"
        class="disc-comp"
        :album="album"
      ></Disc>
    </div>
  </div>
</template>

<script>
  import Disc from '@/components/Disc.vue';
  import HeaderComp from '@/components/HeaderComp.vue';
  import axios from 'axios';

  export default {
    name: 'App',
    components: {
      Disc,
      HeaderComp,
    },
    data() {
      return {
        albums: [],
      };
    },
    created() {
      this.getDisc();
    },
    methods: {
      getDisc() {
        axios
          .get('https://flynn.boolean.careers/exercises/api/array/music')
          .then(re => {
            this.albums = re.data.response;
            console.log(this.albums);
          });
      },
    },
  };
</script>

<style lang="scss">
  /* fonts */
  @import '~@fontsource/montserrat/index.css';
  @import '~@fontsource/montserrat/700.css';
  /* parcials */
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .header-logo {
    width: 6.5vh;
    padding-left: 10px;
  }

  // contenitore dischi

  .main-cont {
    width: 93vw;
    margin: auto;
    @include flex(row, center, flex-start);
    flex-wrap: wrap;
  }
  // componente disco
  .disc-comp {
    background-color: $header-col;
    flex-basis: calc(100% / 8 - 15px);
    height: 35vh;
    margin-right: 15px;
    margin-bottom: 10px;
  }
</style>
