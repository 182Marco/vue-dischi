<template>
  <div id="app">
    <HeaderComp class="header">
      <img class="header-logo" src="@/assets/logo.png" alt="logo" />
    </HeaderComp>
    <div class="main-cont">
      <HideShow class="HideShow" :title="'Click to see all your albums:'">
        <Disc
          v-for="(album, i) in albums"
          :key="i"
          class="disc-comp"
          :album="album"
          :showAll="true"
          :select="false"
        ></Disc>
      </HideShow>
    </div>
    <!-- x ricordare la sintassi quando copierò da mie vecchie repositories -->
    <!-- VERSIONE CON FUNZIONE IN SCRIPT -->
    <!-- <SelectComp @changeSelected="chngeSelection($event)" :generi="generi" /> -->
    <!-- VERSIONE CON FUNZIONE DIRETTAMENTE IN HTML -->
    <div class="main-cont">
      <SelectComp @changeSelected="select = $event" :generi="generi" />
    </div>
    <div class="main-cont">
      <HideShow :title="'Click to see only the genre you\'ve chosen:'">
        <Disc
          v-for="(album, i) in albums"
          :key="i"
          class="disc-comp"
          :album="album"
          :showAll="false"
          :select="select"
        ></Disc>
      </HideShow>
    </div>
    <div class="main-cont">
      <HideShow :title="'Click to see just the albums you like!'">
        <Disc
          v-for="(album, i) in albums"
          :key="i"
          class="disc-comp"
          :album="album"
          :showAll="false"
          :select="false"
        ></Disc>
      </HideShow>
    </div>
  </div>
</template>

<script>
  import Disc from '@/components/Disc.vue';
  import HeaderComp from '@/components/HeaderComp.vue';
  import SelectComp from '@/components/SelectComp.vue';
  import HideShow from '@/components/HideShow.vue';

  import axios from 'axios';

  export default {
    name: 'App',
    components: {
      Disc,
      HeaderComp,
      SelectComp,
      HideShow,
    },
    data() {
      return {
        albums: [],
        generi: [],
        select: null,
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
            // aggiungere una proprità like ai dati
            this.addLikeProp(re.data.response);
            // ottenere array con solo generi senza ripetizioni
            this.createArOfGen(re.data.response);
          });
      },
      addLikeProp(rowData) {
        this.albums = rowData.map(e => ({ ...e, like: false }));
      },
      createArOfGen(rowData) {
        this.generi = rowData
          .map(e => e.genre)
          .filter((e, i, a) => a.indexOf(e) === i);
      },
      // VERSIONE CON FUNZIONE IN SCRIPT
      // chngeSelection(slected) {
      //   this.select = slected;
      // },
      prova() {
        console.log(this.select);
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

  .header,
  .HideShow {
    margin-bottom: 5.5vh;
  }

  .header-logo {
    width: 6.5vh;
    padding-left: 10px;
  }

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

  // contenitore dischi
  .main-cont {
    width: 93vw;
    margin: auto;
    @include flex(row, flex-start, flex-start);
    flex-wrap: wrap;
  }
  // componente disco
  .disc-comp {
    background-color: $header-col;
    height: 35vh;
    margin-right: 15px;
    margin-bottom: 10px;
    flex-basis: calc(100% / 8 - 15px);
    @include media-desk-first(full-desktop) {
      flex-basis: calc(100% / 7 - 15px);
    }
    @include media-desk-first(desktop) {
      flex-basis: calc(100% / 6 - 15px);
    }
    @include media-desk-first(s-desktop) {
      flex-basis: calc(100% / 5 - 15px);
    }
    @include media-desk-first(xs-desktop) {
      flex-basis: calc(100% / 4 - 15px);
    }
    @include media-desk-first(l-tablet) {
      flex-basis: calc(100% / 3 - 15px);
      height: 40vh;
    }
    @include media-desk-first(tablet) {
      flex-basis: calc(100% / 2 - 15px);
      height: 45vh;
    }
    @include media-desk-first(s-tablet) {
      flex-basis: calc(100% / 1 - 15px);
      height: 63vh;
    }
    @include media-desk-first(xs-tablet) {
      height: 52vh;
    }
    @include media-desk-first(phone) {
      height: 57vh;
    }
  }
</style>
