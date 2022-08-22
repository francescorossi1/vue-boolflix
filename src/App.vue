<template>
  <div>
    <MainHeader @forwarded-text="getResults" />
    <MainSection :movies-array="movies" :series-array="series" />
  </div>
</template>

<script>
import axios from 'axios'
import MainHeader from './components/MainHeader.vue'
import MainSection from './components/MainSection.vue'


export default {
  name: 'App',
  components: {
    MainHeader,
    MainSection
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
    searchResults(endpoint, array) {

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
    getResults(value) {
      this.setSearchText(value)
      if (!this.searchText) return
      this.searchResults('/search/movie', 'movies');
      this.searchResults('/search/tv', 'series')
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
