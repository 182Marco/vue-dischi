<template>
  <div>
    <label for="search"
      >Search for title,author or year to filrer albums in all the
      sections:</label
    >
    <input
      v-model.trim="searchedText"
      type="text"
      name=""
      id="search"
      placeholder="Search for title,author or year to filrer albums in all the sections:"
      @keyup="$emit('changeText', searchedText)"
    />
  </div>
</template>

<script>
  export default {
    name: 'SearchComp',
    data() {
      return {
        searchedText: '',
      };
    },
  };
</script>

<style scoped lang="scss">
  @import '@/scss/var';
  @import '@/scss/reset';
  @import '@/scss/mixins';

  label {
    display: none;
    @include media-desk-first(xs-desktop) {
      display: inline-block;
      font-size: calc(0.6rem + 0.4vw);
      margin-left: 10px;
    }
  }

  div {
    width: 100%;
  }
  div,
  input {
    color: $light-txt;
    font-size: 1rem;
  }
  input {
    margin-left: 20px;
    width: 100%;
    background-color: transparent;
    border: none;
    border-bottom: 1px solid $brand;
    border-radius: $boderRadForInputs;
    @include media-desk-first(xs-desktop) {
      margin-left: 5px;
    }
    &:focus {
      outline: none;
      box-shadow: 0 2px 2px -1px $brand;
    }
  }

  ::placeholder {
    color: $light-txt;
    @include media-desk-first(xs-desktop) {
      color: transparent;
    }
  }
</style>
