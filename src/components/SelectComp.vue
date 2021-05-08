<template>
  <div class="container">
    <label for="choseType">Choose a musical genre</label>
    <div class="wrap">
      <select v-model="selected" name="" id="choseType">
        <option v-for="(e, i) in generi" :key="i">{{ e }}</option>
      </select>
    </div>
    <button @click="prova">vediamo la scelta</button>
  </div>
</template>

<script>
  export default {
    name: 'SelectComp',
    props: ['generi'],
    data() {
      return {
        selected: '',
      };
    },
    methods: {
      prova() {
        console.log(this.selected);
      },
    },
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  .container {
    margin: 7vh 0 4vh;
  }

  div {
    @include flex(row, center, center);
    .wrap {
      position: relative;
      background-color: rgba(255, 255, 255, 0.082);
      &::before {
        position: absolute;
        top: 50%;
        transform: translateY(-25%);
        right: 7.5%;
        @include pseudo();
        @include equilateral-triangle(down, 5px, $brand);
        z-index: -10;
      }
    }
  }

  label {
    margin-right: 10px;
    color: $light-txt;
  }

  select {
    width: 150px;
    height: 25px;
    border-radius: 3px;
    padding-left: 10px;
    background-color: transparent;
    color: $light-txt;
    border-color: $light-txt;
    cursor: pointer;
    //   eleiminazioni freccie
    -webkit-appearance: none;
    -moz-appearance: none;
    text-indent: 1px;
    text-overflow: '';
    &:focus {
      outline: none;
    }
  }
</style>
