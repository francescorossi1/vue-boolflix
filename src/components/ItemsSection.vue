<template>
  <div class="bg-secondary">
    <div v-if="itemsArray.length" class="container">
      <h3 class="pt-5">{{ id }}</h3>
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-6 pb-5">
        <ProductCard v-for="item in itemsArray" :key="item.id" :query="query" :product="item" :flags="flags"
          class="col p-2" />
      </div>
    </div>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';
export default {
  name: "ItemsSection",
  props: { itemsArray: Array, id: String, query: String },
  data() {
    return {
      flags: ["it", "en"],
    }
  },
  components: { ProductCard }
}

</script>

<style lang="scss">
</style>