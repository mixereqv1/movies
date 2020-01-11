<template>
  <div class="item">
      <span class="releaseDate"> {{ releaseDate }} </span>
      <span class="forAdult" v-if="forAdult">+18</span>
      <span class="voteAverage"> Ocena: {{ voteAverage }} </span>
      <span :style="style" class="poster"></span>
      <div class="movie">
        <h1> {{ title }} </h1>
        <p> {{ description }} </p>
        <a target="_blank" class="movieLink" :href="movie">Zobacz na: TMDb</a>
      </div>
  </div>
</template>

<script>
const posterURL = 'https://image.tmdb.org/t/p/w185_and_h278_bestv2';
const movieURL = 'https://www.themoviedb.org/movie/';

export default {
  name: 'Item',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      poster: `${posterURL}${this.item.poster_path}`,
      title: this.item.title,
      description: this.item.overview,
      releaseDate: this.item.release_date,
      voteAverage: this.item.vote_average,
      movie: `${movieURL}${this.item.id}`,
      forAdult: this.item.adult,
    };
  },
  computed: {
    style() {
      return `background-image: url('${this.poster}')`;
    },
  },
};
</script>

<style lang="scss" scoped>
    .item {
      width: 90%;
      height: auto;
      min-height: auto;
      display: flex;
      flex-direction: column;
      align-items: center;
      background: #fff;
      border-radius: 15px;
      padding: 20px;
      margin: 10px;
      text-align: center;
      position: relative;

      .releaseDate,
      .voteAverage,
      .forAdult {
        position: absolute;
        top: 10px;
        right: 10px;
        font-weight: 600;
        font-size: 1.1em;
      }

      .voteAverage {
        left: 10px;
        right: auto;

        @media (min-width: 768px) {
          top: auto;
          left: auto;
          bottom: 10px;
          right: 10px;
        }
      }

      .forAdult {
        top: 30px;
        color: #850808;
      }

      @media (min-width: 768px) {
        width: 80%;
        flex-direction: row;
      }

      .poster {
        background-size: contain;
        background-repeat: no-repeat;
        width: 185px;
        height: 278px;
        margin-top: 20px;
      }

      .movie {
        width: 100%;
        height: 60%;

        @media (min-width: 768px) {
          height: 100%;
          width: 70%;
          margin-left: 10px;
        }

        .movieLink {
          // display: inline-flex;
          // width: 100%;
          text-align: left;
          font-size: 1.2em;
          font-weight: 600;
          text-decoration: none;
          color: #1a1a1a;
          cursor: pointer;
        }
      }
    }
</style>
