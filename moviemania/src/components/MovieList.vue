<template>
    <div>
      <ul id="movies">
        <MovieItem
          v-for="(movie, index) in localMovies"
          :key="index"
          :movie="movie"
          :index="index"
          @remove-movie="removeMovie"
        />
      </ul>
      <div class="sorting-buttons">
        <button class="btn btn-success mt-5" @click="sortByTitle">Sortera efter titel</button>
        <button class="btn btn-success mt-5" @click="sortByRating">Sortera efter betyg</button>
      </div>
    </div>
  </template>
  
  <script>
  import MovieItem from './MovieItem.vue';
  
  export default {
    name: 'MovieList',
    components: {
      MovieItem,
    },
    props: {
      movies: Array,
    },
    data() {
      return {
        localMovies: [],
      };
    },
    watch: {
      movies: {
        handler(newMovies) {
          this.localMovies = [...newMovies];
        },
        immediate: true,
        deep: true,
      },
    },
    methods: {
      removeMovie(index) {
        this.$emit('remove-movie', index);
      },
      sortByTitle() {
        this.localMovies.sort((a, b) => a.title.localeCompare(b.title));
      },
      sortByRating() {
        this.localMovies.sort((a, b) => b.rating - a.rating);
      },
    },
  };
  </script>
  