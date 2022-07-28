<template>
  <div id="movies-list">
      <ul v-for="result in resultsArray" :key="result.id">
        <li><strong>Titolo: </strong>{{result.title}}</li>
        <li><strong>Titolo Originale: </strong>{{result.original_title}}</li>
        <li><strong>Lingua Originale: </strong>{{result.original_language}}</li>
        <li><strong>Voto: </strong>{{result.vote_average}}</li>
      </ul>
    </div>
</template>

<script>
export default {
    name: 'MainSection',
    props: {resultsArray: Array}
}
</script>

<style>

</style>