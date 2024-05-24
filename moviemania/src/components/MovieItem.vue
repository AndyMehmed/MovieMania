<template>
    <li :data-grade="movie.rating" :data-title="movie.title">
      {{ movie.title }}
      <img v-for="star in parseInt(movie.rating)" :key="star" src="@/assets/star.png" alt="Star">
      <img src="@/assets/delete.png" alt="Delete movie" class="delete-movie-icon" @click="removeMovie">
    </li>
  </template>
  
  <script>
  export default {
    name: 'MovieItem',
    props: {
      movie: Object,
      index: Number,
    },
    methods: {
      removeMovie() {
        this.$emit('remove-movie', this.index);
      },
    },
  };
  </script>
  
  <style scoped>
  .delete-movie-icon {
    cursor: pointer;
  }
  </style>
  