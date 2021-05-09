<template>
  <div class="comp-Cont">
    <p>
      Loading . . .
      <!-- si posta comprendo progressivamente i puntini per effetto progressione -->
      <span></span>
    </p>
    <!-- barra caricamento -->
    <div class="loadingWrap">
      <div class="increase bar"></div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Loading',
    // props: ['album', 'showAll', 'select', 'deletedGroup', 'searchedText'],
    methods: {},
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .comp-Cont {
    @include flex(column, center, center);
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
    animation: increase 5s infinite;
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
    position: relative;
    @include flex(row, center, center);
    color: $light-txt;
    font-size: 1.5rem;
    font-weight: 700;
    margin: 1vh;
    span {
      position: absolute;
      bottom: 5px;
      right: 0;
      display: inline-block;
      @include width-height(33px, 7px);
      background-color: $main-bg;
      animation: cover-dot 1.6s infinite;
    }
  }

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
