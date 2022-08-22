<template>
  <div>
    <MainHeader @text-searched="getItems" />
    <ItemsSection :items-array="movies" id="Movies" />
    <ItemsSection :items-array="series" id="Series" />
  </div>
</template>

<script>
import axios from 'axios'
import MainHeader from './components/MainHeader.vue'
import ItemsSection from './components/ItemsSection.vue'


export default {
  name: 'App',
  components: {
    MainHeader,
    ItemsSection,
  },
  data() {
    return {
      searchText: '',
      api: {
        baseUri: 'https://api.themoviedb.org/3',
        apiKey: '8879e538b99f81d0c88c4cdd01f5dc49',
        language: 'it-IT'
      },
      movies: [],
      series: []
    }
  }, computed: {

  },
  methods: {
    setSearchText(value) {
      this.searchText = value
    },
    searchItems(endpoint, array) {

      const { baseUri, apiKey, language } = this.api

      const config = {
        params: {
          api_key: apiKey,
          language,
          query: this.searchText,
        }
      }
      axios.get(`${baseUri}${endpoint}`, config)
        .then((res) => {
          this[array] = res.data.results
        })
    },
    getItems(value) {
      this.setSearchText(value)
      if (!this.searchText) return
      this.searchItems('/search/movie', 'movies');
      this.searchItems('/search/tv', 'series')
    }
  }
}
</script>

<style lang="scss">
@import 'bootstrap';

ul {
  padding: 0;

  li {
    list-style-type: none;
  }
}
</style>
