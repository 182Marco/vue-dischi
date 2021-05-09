<template>
  <div class="comp-Cont">
    <p class="precentage">{{ precentage }}%</p>
    <p>
      Loading . . .
      <!-- span che si sposta comprendo progressivamente i puntini per effetto progressione -->
      <span></span>
    </p>
    <!-- barra caricamento -->
    <div class="loadingWrap">
      <!-- scritta percentuale di caricamento sopra barra  -->
      <div class="increase bar"></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Loading',
    data() {
      return {
        precentage: 0,
        int: null,
      };
    },
    created() {
      this.int = setInterval(this.increasePerc, 43);
    },
    methods: {
      increasePerc() {
        this.precentage < 100 ? this.precentage++ : clearInterval(this.int);
      },
    },
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .comp-Cont {
    position: relative;
    @include flex(column, center, center);
  }
  //   percentuale caricamento sopra la barra stessa
  .precentage {
    // creare un bordo intorno al testo
    text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
    // ****************
    position: absolute;
    left: 50%;
    bottom: 27%;
    transform: translateX(-50%);
    margin: 0;
  }
  .loadingWrap {
    @include width-height(40vw, 1vw);
    width: 40vw;
    height: 5vh;
    border: 10px solid $header-col;
    border-radius: 20px;
    overflow: hidden;
  }
  .increase.bar {
    height: 100%;
    background-color: $brand;
  }

  .increase {
    animation: increase 5s;
  }

  @keyframes increase {
    from {
      width: 0;
    }
    to {
      width: 100%;
    }
  }

  //   parte dei testi

  p {
    // border: 1px solid white;
    position: absolute;
    left: 50%;
    bottom: 80%;
    transform: translateX(-50%);
    @include flex(row, center, center);
    color: $light-txt;
    font-size: 1.5rem;
    font-weight: 700;
    span {
      position: absolute;
      bottom: 5px;
      right: 0;
      display: inline-block;
      @include width-height(33px, 7px);
      background-color: $main-bg;
      animation: cover-dot 1.6s linear infinite;
    }
  }

  //   effetto progressione dei puntini

  @keyframes cover-dot {
    0% {
      right: 0;
    }
    32% {
      right: 0;
    }
    33% {
      right: -10px;
    }
    43% {
      right: -10px;
    }
    60% {
      right: -10px;
    }
    61% {
      right: -24px;
    }
    80% {
      right: -24px;
    }
    81% {
      right: -43px;
    }
    100% {
      right: -43px;
    }
  }
</style>
