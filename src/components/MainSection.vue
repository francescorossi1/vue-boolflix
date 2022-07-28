<template>
<div>
    <div id="movies-list" v-if="moviesArray">
        <ul v-for="movie in moviesArray" :key="movie.id">
          <li><strong>Titolo: </strong>{{movie.title}}</li>
          <li><strong>Titolo Originale: </strong>{{movie.original_title}}</li>
          <li><strong>Lingua Originale: </strong>{{movie.original_language}}</li>
          <li><strong>Voto: </strong>{{movie.vote_average}}</li>
        </ul>
      </div>
    <div id="series-list" v-if="seriesArray">
        <ul v-for="series in seriesArray" :key="series.id">
          <li><strong>Titolo: </strong>{{series.name}}</li>
          <li><strong>Titolo Originale: </strong>{{series.original_name}}</li>
          <li><strong>Lingua Originale: </strong>{{series.original_language}}</li>
          <li><strong>Voto: </strong>{{series.vote_average}}</li>
        </ul>
      </div>
</div>
</template>

<script>
export default {
    name: 'MainSection',
    props: {moviesArray: Array, seriesArray: Array}
}
</script>

<style>

</style>