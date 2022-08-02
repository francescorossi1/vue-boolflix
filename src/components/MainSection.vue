<template>
  <div>
    <div v-if="moviesArray.length">
      <h3>Movies</h3>
      <ProductCard v-for="movie in moviesArray" :key="movie.title" :product="movie" :posterSrc="posterSrc"
        :flags="flags" />
    </div>
    <div v-if="seriesArray.length">
      <h3>Series</h3>
      <ProductCard v-for="series in seriesArray" :key="series.title" :product="series" :posterSrc="posterSrc"
        :flags="flags" />
    </div>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';
export default {
  name: "MainSection",
  props: { moviesArray: Array, seriesArray: Array },
  data() {
    return {
      flags: ["it", "en"],
      posterSrc: { baseUri: "https://image.tmdb.org/t/p/", size: "w342/" },
    }
  },
  components: { ProductCard }
}

</script>

<style>
</style>