<template>
    <div class="card p-2 border-0">
        <img v-if="product.poster_path != null" :src="posterSrc.baseUri + posterSrc.size + product.poster_path"
            :alt="product.title" class="img-fluid rounded-1">
        <img v-else src="../assets/img/no-poster.jpg" alt="no poster">
        <div class="card card-hover">
            <ul class="card-body">
                <li><strong>Titolo: </strong>{{ product.title || product.name }}</li>
                <li><strong>Titolo Originale: </strong>{{ product.original_title || product.original_name }}</li>
                <li>
                    <strong>Lingua Originale: </strong>
                    <img v-if="flags.includes(product.original_language)"
                        :src="require('../assets/img/' + product.original_language + '.png')"
                        :alt="product.original_language" class="img-fluid w-25">
                    <span v-else>{{ product.original_language }}</span>
                </li>
                <li>
                    <strong>Voto: </strong>
                    <span><i v-for="num in getStars" :key="num" class="fa-solid fa-star text-warning"></i></span>
                    <span><i v-for="num in 5 - getStars" :key="num" class="fa-regular fa-star text-warning"></i></span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "ProductCard",
    props: { product: Object, posterSrc: Object, flags: Array },
    data() {
        return {
            stars: []
        };
    },
    computed: {
        getStars() {
            return Math.ceil(this.product.vote_average / 2);
        }
    },
}
</script>

<style scoped>
.card {
    position: relative;
    background-color: #6C757D;
    cursor: pointer;
}

.card-hover {
    display: none;
    background-color: rgba(0, 0, 0, 0.6);
    color: #fff;
}

.card:hover .card-hover {
    display: block;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
}
</style>