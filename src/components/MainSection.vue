<template>
  <div>
    <div id="movies-list" v-if="moviesArray">
      <h3>Movies:</h3>
      <ul v-for="movie in moviesArray" :key="movie.id">
        <li><strong>Titolo: </strong>{{ movie.title }}</li>
        <li><strong>Titolo Originale: </strong>{{ movie.original_title }}</li>
        <li>
          <strong>Lingua Originale: </strong>
          <img v-if="flags.includes(movie.original_language)"
            :src="require('../assets/img/' + movie.original_language + '.png')" :alt="movie.original_language">
          <span v-else>{{ movie.original_language }}</span>
        </li>
        <li><strong>Voto: </strong>{{ movie.vote_average }}</li>
      </ul>
    </div>
    <div id="series-list" v-if="seriesArray">
      <h3>Series:</h3>
      <ul v-for="series in seriesArray" :key="series.id">
        <li><strong>Titolo: </strong>{{ series.name }}</li>
        <li><strong>Titolo Originale: </strong>{{ series.original_name }}</li>
        <li>
          <strong>Lingua Originale: </strong>
          <img v-if="flags.includes(series.original_language)"
            :src="require('../assets/img/' + series.original_language + '.png')" :alt="series.original_language">
          <span v-else>{{ series.original_language }}</span>
        </li>
        <li><strong>Voto: </strong>{{ series.vote_average }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainSection',
  props: { moviesArray: Array, seriesArray: Array },
  data() {
    return {
      flags: ['it', 'en']
    }
  }
}
</script>

<style>
</style>