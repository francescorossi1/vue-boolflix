<template>
    <header>
        <SearchBar @text-searched="forwardText" />
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
        forwardText(value) {
            this.text = value
            this.$emit('forwarded-text', this.text)
        }
    },
    components: { SearchBar }
}
</script>

