<template>
  <div>
    <MainHeader @forwarded-text="searchResults"/>
    <MainSection :movies-array="movies" :series-array="series"/>
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
      baseUri: 'https://api.themoviedb.org/3',
      apiKey: '8879e538b99f81d0c88c4cdd01f5dc49',
      movies: [],
      series: []
    }
  }, computed: {

  },
  methods: {
    setSearchText(value){
      this.searchText = value
    },
    searchMovies() {
      axios.get(`${this.baseUri}/search/movie/?api_key=${this.apiKey}&language=it&query=${this.searchText}`)
        .then((res) => {
          return this.movies = res.data.results.map((result)=>{
            const {id, title, original_title, original_language, vote_average} = result
            return {id, title, original_title, original_language, vote_average}
          })
        })
    },
    searchSeries() {
      axios.get(`${this.baseUri}/search/tv/?api_key=${this.apiKey}&language=it&query=${this.searchText}`)
        .then((res) => {
          return this.series = res.data.results.map((result)=>{
            const {id, name, original_name, original_language, vote_average} = result
            return {id, name, original_name, original_language, vote_average}
          })
        })
    },
    searchResults(value){
      this.setSearchText(value)
      if (!this.searchText) return
        this.searchMovies();
        this.searchSeries()
    }
  }
}
</script>

<style lang="scss">
</style>
