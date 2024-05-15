<template>
  <section id="movie-results">
    <ul id="movie-list">
      <li v-for="movie in movies" :key="movie.imdbID">
        <h3>{{ movie.Title }}</h3>
        <img :src="movie.Poster" alt="Movie Poster">
        <span>{{ movie.Year }}</span>
        <span v-for="star in parseInt(movie.Rating)" :key="star">★</span>
        <button @click="removeMovie(movie.imdbID)">X</button>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: ['movies'],
  methods: {
    removeMovie(imdbID) {
      this.$emit('remove', imdbID);
    }
  }
};
</script>
  
  <style scoped>
  /* Din CSS för movie-results kan gå här */
  </style>
  
  <!-- eslint-disable-next-line vue/no-unused-vars -->
  