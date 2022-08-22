<template>
    <header class="navbar bg-black">
        <div class="container d-flex justify-content-between">
            <h1 class="text-danger">Boolflix</h1>
            <SearchBar @text-searched="textSearched" />
        </div>
    </header>
</template>

<script>
import SearchBar from './SearchBar.vue'
export default {
    name: "MainHeader",
    data() {
        return {
            text: ''
        };
    }, methods: {
        textSearched(value) {
            this.text = value
            this.$emit('text-searched', this.text)
        }
    },
    components: { SearchBar }
}
</script>

<style lang="scss">
</style>

