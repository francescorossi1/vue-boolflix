<template>
  <div>
    <MainHeader @forwarded-text="searchMovies"/>
    <MainSection :results-array="results"/>
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
      results: []
    }
  }, computed: {
    
  },
  methods: {
    setSearchText(value){
      this.searchText = value
    },
    searchMovies(value) {
      this.setSearchText(value)
      if (!this.searchText) return
      axios.get(`${this.baseUri}/search/movie/?api_key=${this.apiKey}&language=it&query=${this.searchText}`)
        .then((res) => {
          this.results = res.data.results.map((result)=>{
            const {id, title, original_title, original_language, vote_average} = result
            return {id, title, original_title, original_language, vote_average}
          })
        })
    }
  }
}
</script>

<style lang="scss">
</style>
