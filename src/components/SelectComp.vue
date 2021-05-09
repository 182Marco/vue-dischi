<template>
  <div>
    <label for="choseType">Choose a musical genre</label>
    <div class="wrap">
      <select
        @change="$emit('changeSelected', selected)"
        v-model="selected"
        name=""
        id="choseType"
      >
        <option v-for="(e, i) in generi" :key="i">{{ e }}</option>
      </select>
    </div>
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
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  div {
    @include flex(row, flex-start, center);
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
    font-size: 1.7rem;
    font-weight: bold;
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
