<template>
  <div id="app">
    <div class="container">
      <h1>Vår filmlista</h1>
      <MovieForm @add-movie="addMovie" />
      <hr />
      <h2>Filmer</h2>
      <MovieList :movies="movies" @remove-movie="removeMovie" />
    </div>
  </div>
</template>

<script>
import MovieForm from './components/MovieForm.vue';
import MovieList from './components/MovieList.vue';

export default {
  name: 'App',
  components: {
    MovieForm,
    MovieList,
  },
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    addMovie(movie) {
      this.movies.push(movie);
    },
    removeMovie(index) {
      this.movies.splice(index, 1);
    },
  },
};
</script>


