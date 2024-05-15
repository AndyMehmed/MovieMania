<template>
  <div id="app">
    <div class="container">

      <h1>Min filmlista</h1>
      <form @submit.prevent="addMovie">
        <fieldset>
          <legend>Lägg till en film</legend>

          <label for="title-field">Titel:</label>
          <input type="text" id="title-field" class="form-control" v-model="newMovie.title">

          <label for="rating-field">Betyg:</label>

          <select type="text" id="rating-field" class="form-control" v-model="newMovie.rating">
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

      <hr>

      <h2>Filmer</h2>

      <ul>
        <li v-for="(movie, index) in movies" :key="index" :data-grade="movie.rating" :data-title="movie.title">
          {{ movie.title }}
          <img v-for="star in parseInt(movie.rating)" :key="star" src="./assets/star.png" alt="Star">
          <img src="./assets/delete.png" alt="Delete movie" class="delete-movie-icon" @click="removeMovie(index)">
        </li>
      </ul>

    </div>
  </div>
  <div class="sorting-buttons">
      <button @click="sortByTitle">Sortera efter titel</button>
      <button @click="sortByRating">Sortera efter betyg</button>
    </div>
  
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newMovie: {
        title: '',
        rating: '0'
      },
      movies: []
    }
  },
  methods: {
    addMovie() {
      // Validate
      if (this.newMovie.title === '' || this.newMovie.rating === '0') {
        alert("Var god ange både titel och betyg.");
        return;
      }

      // Add movie
      this.movies.push({
        title: this.newMovie.title,
        rating: this.newMovie.rating
      });

      // Reset form
      this.newMovie.title = '';
      this.newMovie.rating = '0';
    },
    removeMovie(index) {
      this.movies.splice(index, 1);
    },
    sortByTitle() {
      this.movies.sort((a, b) => {
        return a.title.localeCompare(b.title);
      });
    },
    sortByRating() {
      this.movies.sort((a, b) => {
        return b.rating - a.rating;
      });
    }
  }
}
</script>

<style>

#movies {
    margin: 0;
    padding: 0;
}

#movies > li {
    list-style: none;
    background-color: #eee;
    margin: 5px;
    padding: 20px;
    box-shadow: 0 0 5px #999;
}

#movies > li > img {
    float: right;
    height: 25px;
    margin-left: 5px;
}

.delete-movie-icon {
    cursor: pointer;
}
</style>