<template>
    <header>
      <h1>Movie Search</h1>
      <input type="text" v-model="searchTerm" @input="searchMovies" placeholder="Sök efter filmer...">
    </header>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchTerm: ''
      };
    },
    methods: {
      searchMovies() {
        if (this.searchTerm.length >= 3) {
          this.$emit('search', this.searchTerm);
        } else {
          this.$emit('reset');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  /* Din CSS för headern kan gå här */
  </style>