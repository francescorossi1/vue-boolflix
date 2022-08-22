<template>
  <div class="bg-secondary">
    <div v-if="itemsArray.length" class="container">
      <h3 class="pt-5">{{ id }}</h3>
      <div class="row pb-5">
        <ProductCard v-for="item in itemsArray" :key="item.title" :product="item" :flags="flags" class="col-2 p-2" />
      </div>
    </div>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';
export default {
  name: "ItemsSection",
  props: { itemsArray: Array, id: String },
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