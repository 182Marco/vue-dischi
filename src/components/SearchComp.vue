<template>
  <div>
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

  div {
    width: 70%;
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
    &:focus {
      outline: none;
      box-shadow: 0 2px 2px -1px $brand;
    }
  }

  ::placeholder {
    color: $light-txt;
  }
</style>
