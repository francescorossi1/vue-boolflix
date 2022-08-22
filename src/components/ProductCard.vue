<template>
    <div>
        <div class="card border-0">
            <img v-if="product.poster_path != null" :src="getPoster" :alt="product.title" class="img-fluid rounded-2">
            <img v-else src="../assets/img/no-poster.jpg" alt="no poster" class="rounded-2">
            <div class="card card-hover">
                <ul class="p-1">
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
                        <span><i v-for="num in 5" :key="num" class="fa-star text-warning"
                                :class="num <= getFullStars ? 'fa-solid' : 'fa-regular'"></i></span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
const posterSrc = "https://image.tmdb.org/t/p/w342";
export default {
    name: "ProductCard",
    props: { product: Object, flags: Array },
    computed: {
        getPoster() {
            return posterSrc + this.product.poster_path
        },
        getFullStars() {
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
    height: 100%;
}

.card-hover {
    display: none;
    background-color: rgba(0, 0, 0, 0.6);
    color: #fff;
    font-size: 12px;
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