<template>
    <ul>
        <li>
            <img v-if="product.poster_path != null" :src="posterSrc.baseUri + posterSrc.size + product.poster_path"
                :alt="product.title">
            <img v-else src="../assets/img/no-poster.jpg" alt="no poster">
        </li>
        <li><strong>Titolo: </strong>{{ product.title || product.name }}</li>
        <li><strong>Titolo Originale: </strong>{{ product.original_title || product.original_name }}</li>
        <li>
            <strong>Lingua Originale: </strong>
            <img v-if="flags.includes(product.original_language)"
                :src="require('../assets/img/' + product.original_language + '.png')" :alt="product.original_language">
            <span v-else>{{ product.original_language }}</span>
        </li>
        <li><strong>Voto: </strong>{{ roundRating }}</li>
    </ul>
</template>

<script>
export default {
    name: 'ProductCard',
    props: { product: Object, posterSrc: Object, flags: Array },
    computed: {
        roundRating() {
            return Math.ceil(this.product.vote_average / 2);
        }
    },
}
</script>

<style>
</style>