<template>
    <form @submit.prevent="onSubmit">
      <fieldset>
        <legend>Lägg till en film</legend>
  
        <label for="title-field">Titel:</label>
        <input type="text" id="title-field" class="form-control" v-model="title">
  
        <label for="rating-field">Betyg:</label>
        <select id="rating-field" class="form-control" v-model="rating">
          <option value="0">Välj betyg här...</option>
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
          <option value="5">5</option>
        </select>
  
        <input type="submit" class="btn btn-success mt-3" value="Spara film">
      </fieldset>
    </form>
  </template>
  
  <script>
  export default {
    data() {
      return {
        title: '',
        rating: '0',
      };
    },
    methods: {
      onSubmit() {
        if (this.title === '' || this.rating === '0') {
          alert("Var god ange både titel och betyg.");
          return;
        }
  
        this.$emit('add-movie', {
          title: this.title,
          rating: this.rating,
        });
  
        this.title = '';
        this.rating = '0';
      },
    },
  };
  </script>