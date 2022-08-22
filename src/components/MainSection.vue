<template>
  <div class="bg-secondary">
    <div v-if="moviesArray.length" class="container">
      <h3 class="pt-5">Movies</h3>
      <div class="row pb-5">
        <ProductCard v-for="movie in moviesArray" :key="movie.title" :product="movie" :posterSrc="posterSrc"
          :flags="flags" class="col-2" />
      </div>
    </div>
    <div v-if="seriesArray.length" class="container">
      <h3 class="pt-5">Series</h3>
      <div class="container row pb-5">
        <ProductCard v-for="series in seriesArray" :key="series.title" :product="series" :posterSrc="posterSrc"
          :flags="flags" class="col-2" />
      </div>
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

<style lang="scss">
</style>