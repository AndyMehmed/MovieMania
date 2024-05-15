<template>
  <div id="app">
    <SearchBar @search="searchMovies" @reset="resetSearchResults" />
    <MovieList :movies="movies" @remove="removeMovie" />
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue';
import MovieList from './components/MovieList.vue';

export default {
  components: {
    SearchBar,
    MovieList
  },
  data() {
    return {
      movies: []
    };
  },
  methods: {
    searchMovies(searchTerm) {
      if (searchTerm.length >= 3) {
        // Här kan du göra något med searchTerm om det behövs i framtiden
      }
    },
    resetSearchResults() {
      this.movies = [];
    },
    removeMovie(imdbID) {
      this.movies = this.movies.filter(movie => movie.imdbID !== imdbID);
      // Här kan du också göra något med imdbID om det behövs i framtiden
    }
  }
};
</script>

<style>
/* Din globala CSS kan gå här */
</style>
