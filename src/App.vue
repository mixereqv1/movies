<template>
  <div class="app">
    <Search />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'debounce';
import Search from './components/Search.vue';

const baseURL = 'https://api.themoviedb.org/3/search/movie?api_key=4076f33084bc57273f90e8fcf48bff6e&language=pl&query=';
console.log(baseURL);

export default {
  name: 'App',
  components: {
    Search,

  },
  data() {
    return {
      searchValue: '',
      step: 0,
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      axios.get(`${baseURL}${this.searchValue}`)
        .then((response) => {
          console.log(response);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .app {
    width: 100%;
    height: 100vh;
    background: crimson;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
