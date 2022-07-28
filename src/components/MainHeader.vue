<template>
  <header>
    <div id="search-bar">
      <input type="text" placeholder="Inserisci i termini di ricerca" v-model="text" @keyup.enter="$emit('text-searched', text)">
      <button @click="$emit('text-searched', text)">Cerca!</button>
    </div>
  </header>
</template>

<script>
export default {
    name: 'MainHeader',
    data(){
        return {
            text: ''
        }
    }
}
</script>

