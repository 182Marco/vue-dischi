<template>
  <div>
    <!-- <label for="search"
      >Search for title,author or year to filrer albums in all the
      sections:</label
    > -->
    <input
      type="text"
      name=""
      id="search"
      placeholder="Search for title,author or year to filrer albums in all the sections:"
    />
  </div>
</template>

<script>
  export default {
    name: 'SearchComp',
    // props: ['album'],
    methods: {},
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
    border-bottom: 2px solid $light-txt;
    border-radius: $boderRadForInputs;
    &:focus {
      outline: none;
      box-shadow: 0 3px 3px -2px $light-txt;
    }
  }

  ::placeholder {
    color: $light-txt;
  }
</style>
