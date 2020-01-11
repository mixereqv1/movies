<template>
  <div :class="[{ flexStart: step === 1 }, 'app']">
    <Search v-model="searchValue" @input="handleInput" />
    <div class="results" v-if="step === 1 && !loading && results">
      <Item v-for="item in results" :item="item" :key="item.id" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'debounce';
import Search from './components/Search.vue';
import Item from './components/Item.vue';

const baseURL = 'https://api.themoviedb.org/3/search/movie?api_key=4076f33084bc57273f90e8fcf48bff6e&language=pl&query=';

export default {
  name: 'App',
  components: {
    Search,
    Item,

  },
  data() {
    return {
      searchValue: '',
      step: 0,
      loading: false,
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      this.loading = true;
      axios.get(`${baseURL}${this.searchValue}`)
        .then((response) => {
          if (response.status === 200) {
            this.loading = false;
            this.step = 1;

            const { data } = response;
            this.results = data.results;
            console.log(data);
          }
        });
    }, 600),
  },
};
</script>

<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800&display=swap');
  *,
  *::before,
  *::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-family: 'Montserrat', sans-serif;
  }
  .app {
    width: 100%;
    min-height: 100vh;
    background: gray;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    &.flexStart {
      justify-content: flex-start;
    }

    .results {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 20px;
    }
  }
</style>
