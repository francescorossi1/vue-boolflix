<template>
    <div id="search-bar">
        <input type="text" placeholder="Inserisci i termini di ricerca" v-model="text"
            @keyup.enter="$emit('text-searched', text)">
        <button @click="$emit('text-searched', text)">Cerca!</button>
    </div>
</template>

<script>
export default {
    name: 'SearchBar',
    data() {
        return {
            text: ''
        }
    }
}
</script>

<style>
</style>